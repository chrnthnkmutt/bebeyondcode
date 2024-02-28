---
author: Charunthon Limseelo, Sirisa Kornnawawat
pubDatetime: 2024-02-29T23:08:56Z
title: Train Your Time Series Data with Azure Data Explorer Part 2
postSlug: timeseries-ade2
featured: false
draft: false
ogImage: https://boatchrnthn.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fdc9f3c9a-ac9d-4d06-b551-6ddd8dfd0ebf%2Fc1e14aac-f3c2-46e9-b65f-458f79af7e20%2F3.png?table=block&id=e943d1c1-fa94-418c-87cc-1c100636b56c&spaceId=dc9f3c9a-ac9d-4d06-b551-6ddd8dfd0ebf&width=2000&userId=&cache=v2
tags:
  - azuredataexplorer
  - datapredict
  - kusto
  - azure
description: This blog will guide you on forecasting the time series dataset on Azure Data Explorer
---

![3.png](https://boatchrnthn.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fdc9f3c9a-ac9d-4d06-b551-6ddd8dfd0ebf%2Fc1e14aac-f3c2-46e9-b65f-458f79af7e20%2F3.png?table=block&id=e943d1c1-fa94-418c-87cc-1c100636b56c&spaceId=dc9f3c9a-ac9d-4d06-b551-6ddd8dfd0ebf&width=2000&userId=&cache=v2)

- This web blog is exclusive only for Be Beyond Code website, Notion Site, and attendees of Global AI Bootcamp 2024 event. No reposting on Medium.
- Additionally, this is Part 2 : Anomaly and Forecasting,. If you want to proceed to Part 1: Time Series Analysis, please proceed by this link : [Click Here](https://bebeyondcode.vercel.app/posts/timeseries-ade1)

Cloud services and IoT devices generate telemetry data that can be used to gain insights such as monitoring service health, physical production processes, and usage trends. Performing time series analysis is one way to identify deviations in the pattern of these metrics compared to their typical baseline pattern.

Kusto Query Language (KQL) contains native support for creation, manipulation, and analysis of multiple time series. With KQL, you can create and analyze thousands of time series in seconds, enabling near real time monitoring solutions and workflows.

This article details time series anomaly detection and forecasting capabilities of KQL. The applicable time series functions are based on a robust well-known decomposition model, where each original time series is decomposed into seasonal, trend, and residual components. Anomalies are detected by outliers on the residual component, while forecasting is done by extrapolating the seasonal and trend components. The KQL implementation significantly enhances the basic decomposition model by automatic seasonality detection, robust outlier analysis, and vectorized implementation to process thousands of time series in seconds.

## **Prerequisites**

- A Microsoft account or a Microsoft Entra user identity. An Azure subscription isn't required.
- Please read on Part 1: Time Series Analysis by this link: [Click Here](https://bebeyondcode.vercel.app/posts/timeseries-ade1)

## **Time series decomposition model**

The KQL native implementation for time series prediction and anomaly detection uses a well-known decomposition model. This model is applied to time series of metrics expected to manifest periodic and trend behavior, such as service traffic, component heartbeats, and IoT periodic measurements to forecast future metric values and detect anomalous ones. The assumption of this regression process is that other than the previously known seasonal and trend behavior, the time series is randomly distributed. You can then forecast future metric values from the seasonal and trend components, collectively named baseline, and ignore the residual part. You can also detect anomalous values based on outlier analysis using only the residual portion. To create a decomposition model, use the function [series_decompose()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-decompose-function.md). The `series_decompose()` function takes a set of time series and automatically decomposes each time series to its seasonal, trend, residual, and baseline components.

For example, you can decompose traffic of an internal web service by using the following query:

```sql
let min_t = datetime(2017-01-05);
let max_t = datetime(2017-02-03 22:00);
let dt = 2h;
demo_make_series2
| make-series num=avg(num) on TimeStamp from min_t to max_t step dt by sid
| where sid == 'TS1'   //  select a single time series for a cleaner visualization
| extend (baseline, seasonal, trend, residual) = series_decompose(num, -1, 'linefit')  //  decomposition of a set of time series to seasonal, trend, residual, and baseline (seasonal+trend)
| render timechart with(title='Web app. traffic of a month, decomposition', ysplit=panels)
```

![https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-decompose-timechart.png](https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-decompose-timechart.png)

- The original time series is labeled **num** (in red).
- The process starts by auto detection of the seasonality by using the function `[series_periods_detect()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-periods-detect-function.md)` and extracts the **seasonal** pattern (in purple).
- The seasonal pattern is subtracted from the original time series and a linear regression is run using the function `[series_fit_line()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-fit-line-function.md)` to find the **trend** component (in light blue).
- The function subtracts the trend and the remainder is the **residual** component (in green).
- Finally, the function adds the seasonal and trend components to generate the **baseline** (in blue).

## **Time series anomaly detection**

The function [series_decompose_anomalies()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-decompose-anomalies-function.md) finds anomalous points on a set of time series. This function calls `series_decompose()` to build the decomposition model and then runs [series_outliers()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-outliers-function.md) on the residual component. `series_outliers()` calculates anomaly scores for each point of the residual component using Tukey's fence test. Anomaly scores above 1.5 or below -1.5 indicate a mild anomaly rise or decline respectively. Anomaly scores above 3.0 or below -3.0 indicate a strong anomaly.

The following query allows you to detect anomalies in internal web service traffic:

```sql
let min_t = datetime(2017-01-05);
let max_t = datetime(2017-02-03 22:00);
let dt = 2h;
demo_make_series2
| make-series num=avg(num) on TimeStamp from min_t to max_t step dt by sid
| where sid == 'TS1'   //  select a single time series for a cleaner visualization
| extend (anomalies, score, baseline) = series_decompose_anomalies(num, 1.5, -1, 'linefit')
| render anomalychart with(anomalycolumns=anomalies, title='Web app. traffic of a month, anomalies') //use "| render anomalychart with anomalycolumns=anomalies" to render the anomalies as bold points on the series charts.
```

![https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-anomaly-detection.png](https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-anomaly-detection.png)

- The original time series (in red).
- The baseline (seasonal + trend) component (in blue).
- The anomalous points (in purple) on top of the original time series. The anomalous points significantly deviate from the expected baseline values.

## **Time series forecasting**

The function [series_decompose_forecast()](https://github.com/MicrosoftDocs/dataexplorer-docs/blob/main/data-explorer/kusto/query/series-decompose-forecast-function.md) predicts future values of a set of time series. This function calls `series_decompose()` to build the decomposition model and then, for each time series, extrapolates the baseline component into the future.

The following query allows you to predict next week's web service traffic:

```sql
let min_t = datetime(2017-01-05);
let max_t = datetime(2017-02-03 22:00);
let dt = 2h;
let horizon=7d;
demo_make_series2
| make-series num=avg(num) on TimeStamp from min_t to max_t+horizon step dt by sid
| where sid == 'TS1'   //  select a single time series for a cleaner visualization
| extend forecast = series_decompose_forecast(num, toint(horizon/dt))
| render timechart with(title='Web app. traffic of a month, forecasting the next week by Time Series Decomposition')
```

![https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-forecasting.png](https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-forecasting.png)

- Original metric (in red). Future values are missing and set to 0, by default.
- Extrapolate the baseline component (in blue) to predict next week's values.

## **Scalability**

Kusto Query Language syntax enables a single call to process multiple time series. Its unique optimized implementation allows for fast performance, which is critical for effective anomaly detection and forecasting when monitoring thousands of counters in near real-time scenarios.

The following query shows the processing of three time series simultaneously:

```sql
let min_t = datetime(2017-01-05);
let max_t = datetime(2017-02-03 22:00);
let dt = 2h;
let horizon=7d;
demo_make_series2
| make-series num=avg(num) on TimeStamp from min_t to max_t+horizon step dt by sid
| extend offset=case(sid=='TS3', 4000000, sid=='TS2', 2000000, 0)   //  add artificial offset for easy visualization of multiple time series
| extend num=series_add(num, offset)
| extend forecast = series_decompose_forecast(num, toint(horizon/dt))
| render timechart with(title='Web app. traffic of a month, forecasting the next week for 3 time series')
```

![https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-scalability.png](https://github.com/MicrosoftDocs/dataexplorer-docs/raw/main/data-explorer/media/anomaly-detection/series-scalability.png)

## **Summary**

This document details native KQL functions for time series anomaly detection and forecasting. Each original time series is decomposed into seasonal, trend and residual components for detecting anomalies and/or forecasting. These functionalities can be used for near real-time monitoring scenarios, such as fault detection, predictive maintenance, and demand and load forecasting.
