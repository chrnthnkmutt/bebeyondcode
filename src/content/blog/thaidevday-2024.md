---
author: Charunthon Limseelo
pubDatetime: 2024-02-28T09:36:56Z
title: Recapping Thailand Developer Day 2024
postSlug: thaidevday-2024
featured: false
draft: false
tags:
  - azure
  - pysyft
  - openai
  - azureai
  - typescript
  - flutter
  - microsoft
description: Recapping the new innovations on coding from Thailand Developer Day 2024 from many tech collaborators.
canonicalURL: https://medium.com/@boatchrnthn/recapping-thailand-developer-day-2024-267bf4710650
---

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*lVGPLHcdUe8J4sSv6D-naA.png)

Hi developers, welcome to my blog.

So far, I would like to apologize to you guys that I haven’t had much updates about technological news on Medium and my web blog much, but I released some news even on Twitter or Threads. Currently, I do have a research to get it done about Time Series Forecasting. However, I still have some amount of time to write something to you all.

Thailand Developer Day becomes one of the main technological event for every year since 2022, and the speakers will show a lot of new innovations for us to make our productivity better. Last year, we could have seen the qualifying match of Microsoft Imagine Cup 2023 for going to Asian round, which was very interesting to cheer on young talents’ innovations. For this year is a little bit rush and the event took only three hours, but still make me impressed. In this blog, I am going to recap the significant features of the event for you.

## The Next Generation of (x) developers

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*6I5amllH1o4l_yf1_0KV2g.png)

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*5fqz_mcI370zGweQaFok_g.png)

This is quite special session for this collaboration between Microsoft and BorntoDev because there are a lot of free courses and certifications from both companies to let us study and achieve it for your portfolio or resume for your work application. So far, we can obtain the skill from what we learn from both website and having a sandbox lab to try on. I could possibly say that it’s gonna be good opportunity for everyone to learn on new things.

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*N-XUOk0zLXQYM1__nhJy7w.png)

Some of the key features that I obtain from this session would be as following:

- In today's tech landscape, generative AI tools like ChatGPT, GithubCopilot, and others are revolutionizing development. They empower solo developers to create games and SaaS products faster and more efficiently than ever before.
- Generative AI is leveling the playing field, enabling small players to innovate quickly. But choosing the right tech stack remains crucial. Developers must balance skill, adaptability, and innovation to succeed in this rapidly evolving environment.
- Generative AI enhances human creativity—it's a tool, not a replacement. Initiatives like the Dev Init Campaign provide real-world scenarios for developers to explore and innovate.
- In conclusion, the next generation of developers embraces generative AI, pushing boundaries and shaping the future of technology. It's a fusion of human ingenuity and machine intelligence, limited only by imagination.

## Azure App Service: The easy way to build and deploy REST APIs

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*CqWzT8rFfrWba5tYTop7XA.jpeg)

Creating a YouTube clone might seem like a daunting task, but with Azure App Service, it becomes remarkably straightforward. Azure App Service offers a platform for building, deploying, and scaling web apps and APIs with ease. In this section, I would like to sum up on what P’Aeff had explained to us real quick as follows.

- Azure App Service provides a fully managed platform for hosting web applications and APIs. With its seamless integration with Azure services and robust development tools, Azure App Service streamlines the development and deployment process. To begin, you can create a new Azure App Service instance directly from the Azure portal. Once created, you have the flexibility to choose your preferred programming language, but for this case, P’Aeff would like to use Node.js.
- With Azure App Service, you can leverage your favorite frameworks and libraries to build powerful REST APIs. Additionally, Azure App Service provides the necessary infrastructure to support your development environment. Azure App Service handles the underlying infrastructure, including load balancing, auto-scaling, and security, allowing you to concentrate on building your application logic.
- Deploying your REST APIs with Azure App Service is a breeze. You can deploy your code directly from your local development environment using Git, GitHub, Azure DevOps, or Docker containers. Azure App Service seamlessly integrates with popular CI/CD pipelines, enabling automated deployments and continuous integration workflows.
- Once deployed, your REST APIs are instantly accessible over the internet, allowing clients to interact with your YouTube clone programmatically. Azure App Service provides built-in monitoring and diagnostics tools, giving you visibility into your application's performance and health.

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*kD-NmzJmrwC3wX-g8Of0zQ.jpeg)

Another thing that I would to mention on this session is how P’Aeff is very creative for himself to build up his own presentation by coding with JavaScript and Markdown. By the way, I just do only coding with LaTeX, which is better on adjusting. However, don’t make yourself in the stress, so don’t try it would be better.

## Develop A Virtual Assistant with Azure OpenAI Services and Azure AI Speech

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*jbYXlfko65yh4KNThMmW1Q.jpeg)

You may wonder that where P’Job Jirachai is, but you see **Frieren** (フリーレン, *Furīren*) instead in front of you. Now, you may be surprised because P’Job dressed as Frieren this event, and the suit is given by P’Aom Kongkiet, but P’Chang doesn’t dress it for himself and ask P’Job to dress up instead. By the way, I would like to recap on what P’Job had said from his session about building text-to-speech virtual assistant.

- In today's era of advanced technology, creating a virtual assistant has become more accessible and dynamic than ever before. With the powerful capabilities of Azure OpenAI Service and Azure AI Speech, coupled with innovative features like live2d Cubism for character animation, developers can craft immersive and interactive virtual assistants that engage users in meaningful conversations.
- One of the key elements in crafting a captivating virtual assistant is character animation. In the demo, P’Job use **Fern’s** (フェルン, *Ferun*) 2D action figure to be his virtual assistant. With live2d Cubism, P’Job can bring characters to life with fluid movements and expressions. The modeling editor allows for precise customization, while features like Photoshop marking enable detailed facial expressions, including mouth, eye, and eyebrow movements. This adds depth and personality to the virtual assistant, enhancing the user experience.
- Azure OpenAI Service enables developers to integrate advanced natural language processing capabilities into their virtual assistants. By creating meta prompts with ChatGPT, developers can generate dynamic responses that adapt to user input, making conversations more natural and engaging. This allows the virtual assistant to understand context, intent, and sentiment, delivering personalized interactions tailored to each user.
- Lip synchronization, or syncing mouth movements with speech, is essential for creating a realistic virtual assistant experience. Azure AI Speech offers robust text-to-speech functionality, allowing developers to generate lifelike speech in real-time. By synchronizing mouth movements with speech output, developers can create seamless interactions that mimic human conversation, enhancing the immersion and realism of the virtual assistant.
- To ensure a seamless user experience across conversations, it's crucial to attach/upload logs to continuous conversations within the same scope. This enables the virtual assistant to maintain context and remember previous interactions, facilitating more natural and fluid conversations over time. By leveraging Azure's logging capabilities, developers can track user interactions, analyze patterns, and optimize the virtual assistant's performance and responsiveness.

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*BkJTu8AX_9Riyjgzu6SmgA.jpeg)

At the end of the session, P’Job introduced us the Speech Studio inside Azure AI, which working like the demo above, but you are no need to do the animation by ourselves, just filling the prompt and generate the video and sound for it. That could be simple. But if you want some customized model like the session above, you can visit and follow the instruction from this repository >> [https://github.com/antronic/AzureOpenAI-Live2DChatbot](https://github.com/antronic/AzureOpenAI-Live2DChatbot)

## Introduction to Remote Data Science with PySyft

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*Y-ebTIWHWlroxkBHeZ_djg.jpeg)

In today's data-driven world, organizations are increasingly exploring ways to collaborate and share data while maintaining privacy and security. PySyft, a powerful framework for remote data science, offers a solution to these challenges by enabling secure and privacy-preserving collaboration among organizations. In this session, P’James Kanin explored how PySyft facilitates remote data science and addresses concerns related to partnership and agreements.

### **Partnership and Agreement Concerns**

When organizations collaborate on data science projects, several concerns arise regarding privacy, accessibility, data leaks, and ownership of data:

- **Privacy of Data:** Organizations need assurance that their sensitive data remains private and confidential throughout the collaboration process.
- **Accessibility:** Collaborators require seamless access to data and resources, regardless of their physical location or organizational boundaries.
- **Data Leak:** There's a risk of data leakage or unauthorized access when sharing sensitive information across organizations.
- **Ownership of Data:** Clarifying ownership rights and responsibilities is essential to prevent disputes and ensure fair collaboration.

### Solution with PySyft

PySyft offers innovative solutions to address these concerns and facilitate secure and collaborative remote data science:

- **Remote Execution:** PySyft allows organizations to perform computations on remote data without exposing the raw data itself. Through techniques like federated learning and secure multi-party computation (MPC), computations can be securely executed across distributed data sources while preserving privacy.
- **Search & Example Data:** PySyft provides tools for searching and accessing example datasets without revealing the underlying data. This enables organizations to explore and analyze data samples without compromising privacy or security.

At its core, PySyft empowers organizations to collaborate on data science projects while safeguarding sensitive information and preserving privacy. By leveraging cryptographic techniques and decentralized architectures, PySyft enables secure and privacy-preserving computations across distributed datasets.

Through partnerships and agreements facilitated by PySyft, organizations can harness the collective power of data while upholding privacy, security, and data ownership rights. As the field of remote data science continues to evolve, PySyft remains at the forefront, driving innovation and enabling collaborative breakthroughs in data-driven research and analysis.

## Making Recursive Type in TypeScript

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*-Xl9FsrwkiD3bVosL9o_RA.jpeg)

In the realm of advanced type-level programming, the ability to create recursive types is paramount for building flexible and expressive codebases. Let's explore on P’Aom session on how tools like tRCP, Prisma, Elysia, and Prism enable us to harness the power of recursive types while addressing key issues and simplifying development workflows.

- Tools like tRCP, Prisma, Elysia, and Prism serve as enablers for developers seeking to leverage recursive types effectively. These frameworks provide intuitive patterns and abstractions that simplify complex type definitions and promote code reusability across projects.
- Despite the benefits, working with recursive types can pose challenges, especially within the TypeScript ecosystem. TypeScript's type system, while powerful, is Turing complete, as evidenced by issue #14833 in GitHub, where developers have created calculators and even likened it to a virtual machine within a virtual machine—a humorous take on the language's expressive capabilities.
- Innovations in coding style libraries, such as GraphQL String, offer seamless integration without the need for command-line interfaces (CLIs) or parsers. Elysia, with its latest features, facilitates code migration between backend and frontend environments using Prisma, enhancing developer productivity and code maintainability.
- The **`Generic<T>`** construct emerges as a powerful tool for handling recursive types, offering flexibility and type safety across various scenarios. By employing techniques like template literals and accepting n tags, developers can construct intricate type hierarchies and enforce constraints within their codebases.

```tsx
type TreeNode<T> = {
  value: T;
  children: TreeNode<T>[];
};

const tree: TreeNode<number> = {
  value: 1,
  children: [
    {
      value: 2,
      children: [],
    },
    {
      value: 3,
      children: [
        {
          value: 4,
          children: [],
        },
      ],
    },
  ],
};
```

## Flutter in 2024

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*jPfXMXQm287u3B5nRXre0g.jpeg)

In this session, P’Krisada guided us on the new updates of Flutter Framwork on current stable version, which is 3.19, released on past Valentine’s Day. Here are some minor updates for this version from this session.

- **Gemini API & AI Integration**: Introduction of the Google AI Dart SDK beta, enabling generative AI features in Dart or Flutter apps with Gemini models.
- **Framework Enhancements**: Improvements to scrolling behavior, bug fixes for SingleChildScrollView and ReorderableList, and updates to TableView widget.
- **New Widgets & Styles**: Addition of AnimationStyle widget, SegmentedButton.styleFrom method, and Adaptive Switch for a native look on macOS and iOS.
- **Engine Progress**: Advancements in Impeller for Android OpenGL and Vulkan, including performance optimizations and new features like Glyph Information and GPU tracing.

This release also includes various API improvements, performance optimizations, and support for Windows Arm64. For a detailed overview, refer to the release notes and change log. For more information, please visit at [What’s new in Flutter 3.19. Revolutionizing App Development with… | by Kevin Chisholm | Flutter | Feb, 2024 | Medium](https://medium.com/flutter/whats-new-in-flutter-3-19-58b1aae242d2)

## Conclusion

I could possibly say that I really hype on this event very much because there are a lot of new innovations from many innovators in Thailand to show us in the center of Siam Paragon, with about 200-300 attendees in the event. Additionally, I know that Generative AI quite has an impact to many field of work, but try to use it wisely because **Artificial Intelligence is not a substitute for human intelligence; it is a tool to amplify human creativity and ingenuity.**

Thank you for reading, hope you enjoy my story so far and see you on next one.
