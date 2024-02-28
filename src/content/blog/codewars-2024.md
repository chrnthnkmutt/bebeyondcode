---
author: Charunthon Limseelo, Phoomparin Mano, Thai Pangsakulyanont
pubDatetime: 2024-02-27T06:08:56Z
title: The Unforgetable CodeWars 2024 Coding Party
postSlug: codewars-2024
featured: true
draft: false
tags:
  - codewars
  - sevenpeakssoftware
  - creatorsgarten
  - Python
  - Go
description: The coding party with challenging and fun at the same time in 2024.
ogImage: https://miro.medium.com/v2/resize:fit:828/format:webp/1*big1F7matGcLrzQob4YqWw.png
canonicalURL: https://medium.com/@boatchrnthn/the-unforgetable-codewars-2024-coding-party-a0bad44498af
---

![Untitled](https://miro.medium.com/v2/resize:fit:828/format:webp/1*big1F7matGcLrzQob4YqWw.png)

## Table of contents

## Hi Developers,

Some of us may know about the event type like “hackathon” before, it’s just like how use the technologies, computers, or programming, to have a competition with each other. In my younger age, I do have some hackathon on making mobile applications since I was in highschool. During the university level, I did not have it yet. So I decided to register on CodeWars 2024 Coding Party for checking my coding level among the developers.

However, I’m not really good at DSA (Data Structure Algorithm) dynamic programming questions much since I really love on Data Science and visualization part right now. 😅 Maybe, I need to have some dynamic coding skills inside my resume sometimes.

## In the Competing Party…

I thought that developers were coming in the stressing mode for competition, but they do enjoy this party very much, like coding and laughing. Also, Seven Peaks and the event organizer provided us free pizza during the competition, which is really delicious so far.

In meantime, I joined the team with P’Phoomparin Mano and P’Thai Pangsakulyanont from Creatorsgarten, to challenge the coding problems in the deeper level. In this competition, you can use any languages you like, such Python, JavaScript, Go, Ruby, C, or even you can use Microsoft Excel to compete it. In the next part of the blog, I would like to show you some questions that have been used for this competition, and how to solve it in Python. However, some questions are quite complicated to let me code on Python, so I use Go language to aid me in this competition.

## Questions 1 (Practice) : Bangkok Numeral Values

You've heard of Roman numerals, but have you heard of Bangkok numerals?

In Bangkok numerals:

```
B = 100
A = 10
N = 1

```

All other letters and spaces are ignored. The order of letters doesn't matter. The Bangkok numeral value is the sum of all letter values.

For example

```
BANANA = 100+10+1+10+1+10 = 132
NEWBIE = 1+100 = 101
MANGO AND STICKY RICE = 10+1+10+1 = 22

```

What is the Bangkok numeral value of:

"QUALIFYING FOR CODE WAR IS QUITE TRICKY, DEMANDING BOTH BRILLIANCE AND AMBITION. PARTICIPANTS MUST BALANCE ANALYTICAL SKILLS AND NIMBLE PROBLEM-SOLVING, NAVIGATING THROUGH COMPLEX CHALLENGES WITH SPEED AND INNOVATION. IT'S A BATTLEFIELD REQUIRING ADVANCED CODING KNOWLEDGE, A KNACK FOR SOLVING PUZZLES, AND A DEEP PASSION FOR TECHNOLOGY. ONLY THOSE WITH THE DETERMINATION TO EXCEL AND A KEEN ABILITY TO ANALYZE AND INNOVATE CAN HOPE TO STAND OUT IN THIS COMPETITIVE ARENA."

### Answer and Solution

The answer would be 1241, and this is my Python code.

```python
def bangkok_numerals(s):
    s = s.upper()
    return s.count('B')*100 + s.count('A')*10 + s.count('N')

s = "QUALIFYING FOR CODE WAR IS QUITE TRICKY, DEMANDING BOTH BRILLIANCE AND AMBITION. PARTICIPANTS MUST BALANCE ANALYTICAL SKILLS AND NIMBLE PROBLEM-SOLVING, NAVIGATING THROUGH COMPLEX CHALLENGES WITH SPEED AND INNOVATION. IT'S A BATTLEFIELD REQUIRING ADVANCED CODING KNOWLEDGE, A KNACK FOR SOLVING PUZZLES, AND A DEEP PASSION FOR TECHNOLOGY. ONLY THOSE WITH THE DETERMINATION TO EXCEL AND A KEEN ABILITY TO ANALYZE AND INNOVATE CAN HOPE TO STAND OUT IN THIS COMPETITIVE ARENA."
print(bangkok_numerals(s))
```

## Question 2 (Qualifying) : Year of the Dragon

The year 2024 is especially lucky in China, because:

1. The sum of its digits adds to 8.
2. It is the Year of the Dragon, which happens every 12 years (2000, 2012, 2024, 2036, 2048, etc).

Between the year 2000 and year 4000, how many times will this happen?

### Answer and Solution

The answer would be 14, and this is my Python code.

```python
def dragon_years():
    count = 0
    for year in range(2000, 4001):
        if year % 12 == 8 and sum(int(digit) for digit in str(year)) == 8:
            count += 1
    return count

print(dragon_years())
```

## Question 3 : Prime Numbers

A Prime Number is any integer greater than 1 that is only divisible, with no remainder, by 1 and itself.

- Examples of Prime numbers: 3, 5, 7
- Examples that are not Prime numbers: 9 (divisible by 3), 49 (divisible by 7)

The closest 3 Prime numbers to the number 10 are: 11, 13, and 7

What are the closest 3 Prime numbers to 123456?

- Output each of the 3 numbers
- Provide the **sum** of the 3 numbers as your answer

### Answer and Solution

The answer would be 370345, and here is the solution in Python code.

```python
import math

def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    return True

def find_closest_primes(target, num_primes):
    primes = []
    i = 1
    while len(primes) < num_primes:
        if is_prime(target - i):
            primes.append(target - i)
        if is_prime(target + i) and target + i not in primes:
            primes.append(target + i)
        i += 1
    return primes

# Target number
target_number = 123456

# Find the closest 3 prime numbers
closest_primes = find_closest_primes(target_number, 3)

# Output each of the 3 numbers
for prime in closest_primes:
    print(prime)

# Calculate the sum of the 3 numbers
sum_of_primes = sum(closest_primes)
print("Sum of the 3 numbers:", sum_of_primes)
```

## Question 4 : Maximum Sum

In the array of integers below, find the maximum **consecutive** sum of any number of elements.

Examples:

- The sum of the first 3 elements is -54 + 39 + -2 = -17
- The sum of the element[8] to element[12] is 0 + 22 + 70 + 55 + -57 = 90

```
[-54, 39, -2, -88, 42, -18, -16, -16, 0, 22, 70, 55, -57, 43, -27, 88, 28, 6, 60, -39, -85, 46, -57, 83, 0, -53, 0, 10, 22, -78, 26, -7, 100, -87, 47, 72, 94, -11, -42, 100, 63, -35, 39, 2, 57, -30, -17, -75, 27, 83]
```

### Answer and Solution

The answer is 555. And this is my solution ;)

```python
def max_consecutive_sum(arr):
    max_sum = current_sum = arr[0]
    for num in arr[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum

arr = [-54, 39, -2, -88, 42, -18, -16, -16, 0, 22, 70, 55, -57, 43, -27, 88, 28, 6, 60, -39, -85, 46, -57, 83, 0, -53, 0, 10, 22, -78, 26, -7, 100, -87, 47, 72, 94, -11, -42, 100, 63, -35, 39, 2, 57, -30, -17, -75, 27, 83]
print(max_consecutive_sum(arr))
```

## Question 5: Grab Taxi Driver

Sukhumvit Road is a divided boulevard, with odd numbered Sois (lanes) on the north side and even numbered Sois on the south side, according to the diagram below.

A Grab Taxi driver needs to visit certain Sois in order. They must drive in direction of traffic, so in increasing numbers on the odd side of the street, and in decreasing numbers on the even side of the street.

```
  ------------------>
  1 3 5 7  9 11 13 15
  ===================
  2 4 6 8 10 12 14 16
  <------------------

```

Some journeys need a U-turn. For example: going from Soi 9 to Soi 10.

```
           0-----------.
  1 3 5 7  9 11 13 15  :
  ==================== :
  2 4 6 8 10 12 14 16  :
           x<----------'

```

Some journeys require two U-turns. For example: going from Soi 9 to Soi 5.

```
.---->x    0-----------.
: 1 3 5 7  9 11 13 15  :
: =====================:
: 2 4 6 8 10 12 14 16  :
'----------------------'

```

If a driver needs to visit the numbered Sois in the order below, how many U-turns will they have to make?

```
[2, 8, 10, 4, 6, 2, 10, 3, 11, 7, 8, 11, 15, 12, 5, 7, 14, 2, 7, 14, 13, 7, 5, 12, 15, 11, 4, 11, 4, 11, 10, 5, 8, 2, 14, 2, 3, 10, 9, 11, 6, 14, 1, 14, 12, 2, 9, 15, 8, 7, 3, 14, 8, 2, 12, 7, 5, 3, 10, 9, 12, 3, 8, 11, 2, 4, 10, 6, 13, 15, 4, 5, 13, 3, 6, 3, 8, 7, 4, 1, 4, 8, 6, 5, 3, 14, 10, 2, 6, 9, 3, 11, 12, 2, 1, 15, 9, 4, 13, 2]

```

### Answer and Solution

The answer for this question is 98, and this is my Go Language implementation.

```go
package main

import (
	"fmt"
)

func isEven(n int) bool {
	return n%2 == 0
}

func main() {

	// conditions where you make a U-turn:
	// - odd soi: larger to smaller (2x)
	// - even soi: smaller to larger (2x)
	// - odd soi to even soi, or vice versa

	route := []int{2, 8, 10, 4, 6, 2, 10, 3, 11, 7, 8, 11, 15, 12, 5, 7, 14, 2,
		7, 14, 13, 7, 5, 12, 15, 11, 4, 11, 4, 11, 10, 5, 8, 2, 14, 2, 3, 10, 9, 11,
		6, 14, 1, 14, 12, 2, 9, 15, 8, 7, 3, 14, 8, 2, 12, 7, 5, 3, 10, 9, 12, 3, 8,
		11, 2, 4, 10, 6, 13, 15, 4, 5, 13, 3, 6, 3, 8, 7, 4, 1, 4, 8, 6, 5, 3, 14,
		10, 2, 6, 9, 3, 11, 12, 2, 1, 15, 9, 4, 13, 2}

	uturns := 0

	for i, nxt := range route {
		if i == 0 {
			continue
		}

		prev := route[i-1]

		if isEven(prev) && !isEven(nxt) {
			uturns += 1
			fmt.Printf("%02d >> %02d: U-TURN (even >> odd) [%02d]\n", prev, nxt, uturns)
			continue
		}

		if !isEven(prev) && isEven(nxt) {
			uturns += 1
			fmt.Printf("%02d >> %02d: U-TURN (odd >> even) [%02d]\n", prev, nxt, uturns)
			continue
		}

		if isEven(prev) && (prev < nxt) {
			uturns += 2
			fmt.Printf("%02d >> %02d: U-TURNx2 (even S>>L) [%02d]\n", prev, nxt, uturns)
			continue
		}

		if !isEven(prev) && (prev > nxt) {
			uturns += 2
			fmt.Printf("%02d >> %02d: U-TURNx2 (odd L>>S)  [%02d]\n", prev, nxt, uturns)
			continue
		}

		fmt.Printf("%02d >> %02d: no U-turn            [%02d]\n", prev, nxt, uturns)
	}

	fmt.Println(uturns)
}
```

## Question 6

The large chunk of JSON below represents a tree data structure with the format:

```xml
type Node = {
  id: number;       // always a positive integer
  children: Node[];
}
```

The path from the root [id: 0] to the endpoint [id: 83] is: 0-4-26-83. Note that [id: 83] has no children. The sum of this path is 113.

Which endpoint has the highest total sum path from root?

- Output the sum path
- Provide the *id* as your answer

```json
{
  "id": 0,
  "children": [
    {
      "id": 2263,
      "children": [
        {
          "id": 11251,
          "children": [
            {
              "id": 9626,
              "children": [
                {
                  "id": 3010,
                  "children": [
                    { "id": 760, "children": [] },
                    { "id": 8429, "children": [] }
                  ]
                },
                {
                  "id": 422,
                  "children": [
                    { "id": 9290, "children": [] },
                    { "id": 8230, "children": [] },
                    { "id": 10213, "children": [] },
                    { "id": 8176, "children": [] }
                  ]
                },
                {
                  "id": 3300,
                  "children": [
                    { "id": 3689, "children": [] },
                    { "id": 10239, "children": [] },
                    { "id": 11335, "children": [] },
                    { "id": 9722, "children": [] }
                  ]
                }
              ]
            },
            {
              "id": 9803,
              "children": [
                {
                  "id": 1856,
                  "children": [
                    { "id": 11593, "children": [] },
                    { "id": 3504, "children": [] },
                    { "id": 1465, "children": [] },
                    { "id": 3328, "children": [] }
                  ]
                },
                {
                  "id": 3759,
                  "children": [
                    { "id": 8856, "children": [] },
                    { "id": 9201, "children": [] },
                    { "id": 3797, "children": [] },
                    { "id": 10754, "children": [] }
                  ]
                }
              ]
            },
            {
              "id": 1448,
              "children": [
                {
                  "id": 9812,
                  "children": [
                    { "id": 8310, "children": [] },
                    { "id": 1816, "children": [] },
                    { "id": 9665, "children": [] }
                  ]
                },
                {
                  "id": 11597,
                  "children": [
                    { "id": 11947, "children": [] },
                    { "id": 9397, "children": [] },
                    { "id": 8770, "children": [] }
                  ]
                },
                {
                  "id": 1999,
                  "children": [
                    { "id": 9772, "children": [] },
                    { "id": 1981, "children": [] },
                    { "id": 11841, "children": [] },
                    { "id": 10164, "children": [] },
                    { "id": 12000, "children": [] }
                  ]
                },
                { "id": 913, "children": [] },
                { "id": 3274, "children": [] }
              ]
            },
            {
              "id": 976,
              "children": [
                { "id": 1991, "children": [] },
                { "id": 2052, "children": [] },
                { "id": 9184, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 9144,
          "children": [
            {
              "id": 702,
              "children": [
                { "id": 8149, "children": [] },
                { "id": 3765, "children": [] },
                { "id": 8325, "children": [] }
              ]
            },
            {
              "id": 284,
              "children": [
                { "id": 2590, "children": [] },
                { "id": 1990, "children": [] }
              ]
            },
            {
              "id": 10370,
              "children": [
                { "id": 10314, "children": [] },
                { "id": 591, "children": [] },
                { "id": 10344, "children": [] },
                { "id": 9682, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 9718,
          "children": [
            {
              "id": 2719,
              "children": [
                { "id": 8546, "children": [] },
                { "id": 3261, "children": [] },
                { "id": 9284, "children": [] }
              ]
            },
            {
              "id": 10775,
              "children": [
                { "id": 11488, "children": [] },
                { "id": 10346, "children": [] },
                { "id": 8132, "children": [] },
                { "id": 11316, "children": [] },
                { "id": 10567, "children": [] }
              ]
            }
          ]
        }
      ]
    },
    {
      "id": 1696,
      "children": [
        {
          "id": 8884,
          "children": [
            {
              "id": 1737,
              "children": [
                { "id": 8464, "children": [] },
                { "id": 2723, "children": [] },
                { "id": 9425, "children": [] },
                { "id": 2500, "children": [] }
              ]
            },
            {
              "id": 9195,
              "children": [
                { "id": 618, "children": [] },
                { "id": 278, "children": [] },
                { "id": 9048, "children": [] }
              ]
            },
            {
              "id": 273,
              "children": [
                { "id": 8043, "children": [] },
                { "id": 36, "children": [] },
                { "id": 2738, "children": [] },
                { "id": 10312, "children": [] },
                { "id": 49, "children": [] }
              ]
            },
            {
              "id": 11457,
              "children": [
                { "id": 3768, "children": [] },
                { "id": 1184, "children": [] },
                { "id": 2718, "children": [] }
              ]
            },
            {
              "id": 9464,
              "children": [
                { "id": 11798, "children": [] },
                { "id": 835, "children": [] },
                { "id": 1284, "children": [] },
                { "id": 11066, "children": [] },
                { "id": 1203, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 8072,
          "children": [
            {
              "id": 2928,
              "children": [
                { "id": 101, "children": [] },
                { "id": 2230, "children": [] },
                { "id": 9954, "children": [] },
                { "id": 2210, "children": [] }
              ]
            },
            {
              "id": 9156,
              "children": [
                { "id": 3424, "children": [] },
                { "id": 10112, "children": [] },
                { "id": 271, "children": [] },
                { "id": 2944, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 1621,
          "children": [
            {
              "id": 3277,
              "children": [
                { "id": 2563, "children": [] },
                { "id": 9215, "children": [] },
                { "id": 10389, "children": [] },
                { "id": 117, "children": [] },
                { "id": 1788, "children": [] }
              ]
            },
            {
              "id": 3903,
              "children": [
                { "id": 1331, "children": [] },
                { "id": 3671, "children": [] },
                { "id": 9411, "children": [] },
                { "id": 9710, "children": [] }
              ]
            },
            {
              "id": 8475,
              "children": [
                { "id": 11203, "children": [] },
                { "id": 11487, "children": [] },
                { "id": 1313, "children": [] },
                { "id": 8569, "children": [] }
              ]
            },
            {
              "id": 100,
              "children": [
                { "id": 10193, "children": [] },
                { "id": 8329, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 9940,
          "children": [
            {
              "id": 9897,
              "children": [
                { "id": 3326, "children": [] },
                { "id": 2557, "children": [] },
                { "id": 11426, "children": [] },
                { "id": 444, "children": [] }
              ]
            },
            {
              "id": 9230,
              "children": [
                { "id": 46, "children": [] },
                { "id": 2522, "children": [] },
                { "id": 8057, "children": [] },
                { "id": 8644, "children": [] }
              ]
            },
            {
              "id": 10202,
              "children": [
                { "id": 354, "children": [] },
                { "id": 10409, "children": [] },
                { "id": 982, "children": [] },
                { "id": 1173, "children": [] },
                { "id": 1040, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 1005,
          "children": [
            {
              "id": 3864,
              "children": [
                { "id": 638, "children": [] },
                { "id": 8890, "children": [] },
                { "id": 8978, "children": [] },
                { "id": 9588, "children": [] }
              ]
            },
            {
              "id": 10469,
              "children": [
                { "id": 2000, "children": [] },
                { "id": 8374, "children": [] },
                { "id": 11260, "children": [] },
                { "id": 1310, "children": [] }
              ]
            },
            {
              "id": 2609,
              "children": [
                { "id": 1435, "children": [] },
                { "id": 10827, "children": [] },
                { "id": 1636, "children": [] },
                { "id": 9145, "children": [] }
              ]
            },
            {
              "id": 810,
              "children": [
                { "id": 9157, "children": [] },
                { "id": 2934, "children": [] },
                { "id": 3700, "children": [] },
                { "id": 10989, "children": [] }
              ]
            },
            {
              "id": 1792,
              "children": [
                { "id": 10067, "children": [] },
                { "id": 1230, "children": [] }
              ]
            }
          ]
        }
      ]
    },
    {
      "id": 2029,
      "children": [
        {
          "id": 8049,
          "children": [
            {
              "id": 11584,
              "children": [
                { "id": 2261, "children": [] },
                { "id": 11815, "children": [] },
                { "id": 1937, "children": [] },
                { "id": 2328, "children": [] }
              ]
            },
            {
              "id": 11776,
              "children": [
                { "id": 9866, "children": [] },
                { "id": 3353, "children": [] },
                { "id": 1183, "children": [] }
              ]
            }
          ]
        },
        {
          "id": 11732,
          "children": [
            {
              "id": 11614,
              "children": [
                { "id": 2108, "children": [] },
                { "id": 8935, "children": [] },
                { "id": 11868, "children": [] }
              ]
            },
            {
              "id": 426,
              "children": [
                { "id": 8406, "children": [] },
                { "id": 2382, "children": [] },
                { "id": 11645, "children": [] },
                { "id": 9246, "children": [] }
              ]
            },
            {
              "id": 1722,
              "children": [
                { "id": 10162, "children": [] },
                { "id": 768, "children": [] },
                { "id": 10907, "children": [] }
              ]
            },
            {
              "id": 8190,
              "children": [
                { "id": 1838, "children": [] },
                { "id": 2875, "children": [] },
                { "id": 2834, "children": [] }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

### Answer and Solution

The answers of this questions is 11947, and this is my solution by using Go implementation. But this code might have the error in it, if you can find it then you can email me.

```go
package main

import (
	"encoding/json"
	"fmt"
)

type Node struct {
	Id       int    `json:"id"`
	Children []Node `json:"children"`
}

type Search struct {
	History []Node
	Current *Node
}

// id -> sum
type Results map[int]int

func mapSlice[T any, M any](enum []T, mapper func(T) M) []M {
	n := make([]M, len(enum))
	for i, e := range enum {
		n[i] = mapper(e)
	}
	return n
}

func visit(history []Node, current Node, results Results) {
	// this is an endpoint
	if len(current.Children) == 0 {
		ids := mapSlice[Node, int](history, func(node Node) int {
			return node.Id
		})
		ids = append(ids, current.Id)

		sum := 0
		for _, n := range ids {
			sum += n
		}

		results[current.Id] = sum
	} else {
		for _, child := range current.Children {
			visit(append(history, current), child, results)
		}
	}
}

func main() {
	var root Node
	json.Unmarshal([]byte(jsChunk), &root)

	results := make(Results)
	visit([]Node{}, root, results)

	// fmt.Println(results)
	highid := 0
	highsum := 0

	for id, sum := range results {
		if sum > highsum {
			highid = id
			highsum = sum
		}
	}

	fmt.Printf("Highest ID: %d / sum: %d\n", highid, highsum)
	// Highest ID: 11947 / sum: 38506
}

const jsChunk = `
{"id":0,"children":[{"id":2263,"children":[{"id":11251,"children":[{"id":9626,
"children":[{"id":3010,"children":[{"id":760,"children":[]},{"id":8429,
"children":[]}]},{"id":422,"children":[{"id":9290,"children":[]},{"id":8230,
"children":[]},{"id":10213,"children":[]},{"id":8176,"children":[]}]},
{"id":3300,"children":[{"id":3689,"children":[]},{"id":10239,"children":[]},
{"id":11335,"children":[]},{"id":9722,"children":[]}]}]},{"id":9803,
"children":[{"id":1856,"children":[{"id":11593,"children":[]},{"id":3504,
"children":[]},{"id":1465,"children":[]},{"id":3328,"children":[]}]},
{"id":3759,"children":[{"id":8856,"children":[]},{"id":9201,"children":[]},
{"id":3797,"children":[]},{"id":10754,"children":[]}]}]},{"id":1448,
"children":[{"id":9812,"children":[{"id":8310,"children":[]},{"id":1816,
"children":[]},{"id":9665,"children":[]}]},{"id":11597,"children":[{"id":11947,
"children":[]},{"id":9397,"children":[]},{"id":8770,"children":[]}]},
{"id":1999,"children":[{"id":9772,"children":[]},{"id":1981,"children":[]},
{"id":11841,"children":[]},{"id":10164,"children":[]},{"id":12000,
"children":[]}]},{"id":913,"children":[]},{"id":3274,"children":[]}]},
{"id":976,"children":[{"id":1991,"children":[]},{"id":2052,"children":[]},
{"id":9184,"children":[]}]}]},{"id":9144,"children":[{"id":702,
"children":[{"id":8149,"children":[]},{"id":3765,"children":[]},{"id":8325,
"children":[]}]},{"id":284,"children":[{"id":2590,"children":[]},{"id":1990,
"children":[]}]},{"id":10370,"children":[{"id":10314,"children":[]},{"id":591,
"children":[]},{"id":10344,"children":[]},{"id":9682,"children":[]}]}]},
{"id":9718,"children":[{"id":2719,"children":[{"id":8546,"children":[]},
{"id":3261,"children":[]},{"id":9284,"children":[]}]},{"id":10775,
"children":[{"id":11488,"children":[]},{"id":10346,"children":[]},{"id":8132,
"children":[]},{"id":11316,"children":[]},{"id":10567,"children":[]}]}]}]},
{"id":1696,"children":[{"id":8884,"children":[{"id":1737,
"children":[{"id":8464,"children":[]},{"id":2723,"children":[]},{"id":9425,
"children":[]},{"id":2500,"children":[]}]},{"id":9195,"children":[{"id":618,
"children":[]},{"id":278,"children":[]},{"id":9048,"children":[]}]},{"id":273,
"children":[{"id":8043,"children":[]},{"id":36,"children":[]},{"id":2738,
"children":[]},{"id":10312,"children":[]},{"id":49,"children":[]}]},
{"id":11457,"children":[{"id":3768,"children":[]},{"id":1184,"children":[]},
{"id":2718,"children":[]}]},{"id":9464,"children":[{"id":11798,"children":[]},
{"id":835,"children":[]},{"id":1284,"children":[]},{"id":11066,"children":[]},
{"id":1203,"children":[]}]}]},{"id":8072,"children":[{"id":2928,
"children":[{"id":101,"children":[]},{"id":2230,"children":[]},{"id":9954,
"children":[]},{"id":2210,"children":[]}]},{"id":9156,"children":[{"id":3424,
"children":[]},{"id":10112,"children":[]},{"id":271,"children":[]},{"id":2944,
"children":[]}]}]},{"id":1621,"children":[{"id":3277,"children":[{"id":2563,
"children":[]},{"id":9215,"children":[]},{"id":10389,"children":[]},{"id":117,
"children":[]},{"id":1788,"children":[]}]},{"id":3903,"children":[{"id":1331,
"children":[]},{"id":3671,"children":[]},{"id":9411,"children":[]},{"id":9710,
"children":[]}]},{"id":8475,"children":[{"id":11203,"children":[]},{"id":11487,
"children":[]},{"id":1313,"children":[]},{"id":8569,"children":[]}]},{"id":100,
"children":[{"id":10193,"children":[]},{"id":8329,"children":[]}]}]},
{"id":9940,"children":[{"id":9897,"children":[{"id":3326,"children":[]},
{"id":2557,"children":[]},{"id":11426,"children":[]},{"id":444,
"children":[]}]},{"id":9230,"children":[{"id":46,"children":[]},{"id":2522,
"children":[]},{"id":8057,"children":[]},{"id":8644,"children":[]}]},
{"id":10202,"children":[{"id":354,"children":[]},{"id":10409,"children":[]},
{"id":982,"children":[]},{"id":1173,"children":[]},{"id":1040,
"children":[]}]}]},{"id":1005,"children":[{"id":3864,"children":[{"id":638,
"children":[]},{"id":8890,"children":[]},{"id":8978,"children":[]},{"id":9588,
"children":[]}]},{"id":10469,"children":[{"id":2000,"children":[]},{"id":8374,
"children":[]},{"id":11260,"children":[]},{"id":1310,"children":[]}]},
{"id":2609,"children":[{"id":1435,"children":[]},{"id":10827,"children":[]},
{"id":1636,"children":[]},{"id":9145,"children":[]}]},{"id":810,
"children":[{"id":9157,"children":[]},{"id":2934,"children":[]},{"id":3700,
"children":[]},{"id":10989,"children":[]}]},{"id":1792,"children":[{"id":10067,
"children":[]},{"id":1230,"children":[]}]}]}]},{"id":2029,
"children":[{"id":8049,"children":[{"id":11584,"children":[{"id":2261,
"children":[]},{"id":11815,"children":[]},{"id":1937,"children":[]},{"id":2328,
"children":[]}]},{"id":11776,"children":[{"id":9866,"children":[]},{"id":3353,
"children":[]},{"id":1183,"children":[]}]}]},{"id":11732,
"children":[{"id":11614,"children":[{"id":2108,"children":[]},{"id":8935,
"children":[]},{"id":11868,"children":[]}]},{"id":426,"children":[{"id":8406,
"children":[]},{"id":2382,"children":[]},{"id":11645,"children":[]},{"id":9246,
"children":[]}]},{"id":1722,"children":[{"id":10162,"children":[]},{"id":768,
"children":[]},{"id":10907,"children":[]}]},{"id":8190,"children":[{"id":1838,
"children":[]},{"id":2875,"children":[]},{"id":2834,"children":[]}]}]}]}]}
`
```

## Question 7: Paperfold

An A4 sheet of paper is 210mm wide by 297mm tall. If you fold it once, dividing its *longest* dimension, the result is 210mm wide by 297 / 2 == 148.5 tall.

Using this method, how many times do you need to fold an A4 sheet to fit on a 2mm x 2mm grain of rice?

- Output the final dimensions (in any order)
- Provide the *number of folds* as your answer

### Answer and Solution

The answer of this question is 15 folds, and this is my Python implementation.

```python
width = 210
height = 297
folds = 0

while width > 2 or height > 2:
    if width > height:
        width /= 2
    else:
        height /= 2
    folds += 1

print(f"The number of folds required is {folds}.")
print(f"The final dimensions are {width}mm by {height}mm.")
```

## Question 8: Wordsearch (Semifinal)

A word search puzzle is a grid of letters where your challenge is to find selected words as formed by consecutive letters in a line along the rows or columns of the grid. In this puzzle, a word can only appear forwards (left to right or top to bottom) and we will ignore diagonals.

For example, the grid below:

```
DOG
WLE
PDT
```

contains the words DOG, OLD, and GET.

Find all the words *4 letters* or greater in the word search below. A [dictionary.txt](https://github.com/bangkokrb/codewars-2024/blob/master/data/dictionary.txt) file is provided.

- Output each unique word found
- Provide the **number of words found** as your answer

`CYSCNRLGUNXOFMCBKLBWAWAUC
VNXWHMEXDZJXZSTUYCGDPBNZZ
RQARFLEBQMYTWAZBGUXYRXGMU
HAHZFFAKXJALYEPRLSNJBXDAL
UUAMOWHHYSPXHFTUUCIDFCAPV
ACKIWDGAUAEVHEOPPIPZGSHOA
VLCGJWYSZLUSKFMFKLPYTHONH
GIEBKGIKLTYZZADKLIXRRIRHC
XQJFLIVETSIQPYGCISGUDWWHY
REPTCHJLYZEUTYUTKPTBSWLKS
NKDEIMCLWEMMHVKECDOYIFEZC
JBMFNZILLJLJXZLYWIIGDWSCH
IWPVRBHQFCJHULHFSUAIHBFWE
DENAOCKJITXMONGLASSEMBLYM
MWHYUKXTLHXUDXZACRFOSYMJE
MEHIYHAEDHZXHUNUVLBYZYLCN
WDAZEZCZAUNTVNQDGPFTLDPFD
YOVDDHENCFPGWDTGEUCSHNUHB
DYHJKNXVCFTYPESCRIPTTTAOL
WMJRNDWFQKHJAVASCRIPTAQCC
CLOJURERXUKYOOFTKZWSJOPAW
EKDIPLLAJPJULIARKBUYPHIMQ
YWBCOOQSXIUENXLUYATDXATLZ
YPPLHSPJWEDSVELSSHESZQWKY
UUMFDWTSMTIMNZTTVMNHDCGNQ`

### Solution

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

const wordSearch = `CYSCNRLGUNXOFMCBKLBWAWAUC
VNXWHMEXDZJXZSTUYCGDPBNZZ
RQARFLEBQMYTWAZBGUXYRXGMU
HAHZFFAKXJALYEPRLSNJBXDAL
UUAMOWHHYSPXHFTUUCIDFCAPV
ACKIWDGAUAEVHEOPPIPZGSHOA
VLCGJWYSZLUSKFMFKLPYTHONH
GIEBKGIKLTYZZADKLIXRRIRHC
XQJFLIVETSIQPYGCISGUDWWHY
REPTCHJLYZEUTYUTKPTBSWLKS
NKDEIMCLWEMMHVKECDOYIFEZC
JBMFNZILLJLJXZLYWIIGDWSCH
IWPVRBHQFCJHULHFSUAIHBFWE
DENAOCKJITXMONGLASSEMBLYM
MWHYUKXTLHXUDXZACRFOSYMJE
MEHIYHAEDHZXHUNUVLBYZYLCN
WDAZEZCZAUNTVNQDGPFTLDPFD
YOVDDHENCFPGWDTGEUCSHNUHB
DYHJKNXVCFTYPESCRIPTTTAOL
WMJRNDWFQKHJAVASCRIPTAQCC
CLOJURERXUKYOOFTKZWSJOPAW
EKDIPLLAJPJULIARKBUYPHIMQ
YWBCOOQSXIUENXLUYATDXATLZ
YPPLHSPJWEDSVELSSHESZQWKY
UUMFDWTSMTIMNZTTVMNHDCGNQ`

func validateArgs() {
	if len(os.Args) < 2 {
		fmt.Printf("Usage: %s [dictionary file]\n", os.Args[0])
		os.Exit(1)
	}
}

func main() {
  validateArgs()

	// load and make the dictionary uniform
	f, err := os.Open(os.Args[1])
	if err != nil {
		fmt.Printf("Could not read file")
		os.Exit(1)
	}
	defer f.Close()

	scanner := bufio.NewScanner(f)
	var dictionary []string
	for scanner.Scan() {
    t := scanner.Text()
		if len(t) < 4 {
			// instructions: only 4 letters+ words matter
			continue
		}
		dictionary = append(dictionary, t)
	}

	var matches []string
	rows := strings.Split(wordSearch, "\n")
	for _, row := range rows {
		for _, word := range dictionary {
			if strings.Contains(row, word) {
				matches = append(matches, word)
			}
		}
	}

	var cols []string
	for i := 0; i < len(rows[0]); i++ {
		var sb strings.Builder
		for _, row := range rows {
			sb.WriteByte(row[i])
		}
		cols = append(cols, sb.String())
	}
	for _, col := range cols {
		for _, word := range dictionary {
			if strings.Contains(col, word) {
				matches = append(matches, word)
			}
		}
	}

  // remove duplicates
  seen := make(map[string]int, 0)
  var deduped []string
  for _, m := range matches {
    if seen[m] == 0 {
      deduped = append(deduped, m)
    }
    seen[m] = 1
  }

	fmt.Println(deduped)
  fmt.Println(len(deduped))
}
```

## Question 9: Coins (Semifinal)

- A 10 baht coin weighs 8.5 grams
- A 5 baht coin weighs 6 grams
- A 2 baht coin weighs 4 grams
- A 1 baht coin weighs 3 grams

If i have 9 grams of coins, I could have one 1 baht coin and one 5 baht coin, or three 1 baht coins. That's 2 possible combinations.

If I have 55.5 grams of coins, how many different possible combinations of 1, 2, 5 and 10 baht coins could I have?

### Answer and Solution

The answer is 30 combinations, and this is my Python code.

```python
def count_combinations(total_weight, target_weight, coin_weights, index):
    # If the total weight equals the target weight, we found a valid combination
    if total_weight == target_weight:
        return 1

    # If the total weight exceeds the target weight, or we have exhausted all coin weights, return 0
    if total_weight > target_weight or index >= len(coin_weights):
        return 0

    # Count combinations including the current coin weight
    count_with_current = count_combinations(total_weight + coin_weights[index], target_weight, coin_weights, index)

    # Count combinations excluding the current coin weight
    count_without_current = count_combinations(total_weight, target_weight, coin_weights, index + 1)

    return count_with_current + count_without_current

# Define the weights of the coins
coin_weights = [3, 4, 6, 8.5]

# Target weight
target_weight = 55.5

# Count combinations
combinations = count_combinations(0, target_weight, coin_weights, 0)

print("Number of different possible combinations:", combinations)
```

## Question 10 (Final Round) : Victory Flag

The independent nation of Mattistan has decided their flag will be made from ASCII characters. Specifically, the flag looks like this:

```
+-+-+
|\|/|
+-+-+
|/|\|
+-+-+

```

This flag can be scaled to an arbitrary size N. A size 2 flag looks like this:

```
+--+--+
|\ | /|
| \|/ |
+--+--+
| /|\ |
|/ | \|
+--+--+

```

Write a program that takes any size N and outputs a flag of that size.

Output a flag of size N=5

### Solution

```go
package main

import (
	"fmt"
	"os"
	"strconv"
	"strings"
)

func validateArgs() {
	if len(os.Args) < 2 {
		fmt.Printf("Usage: %s [size of flag]\n", os.Args[0])
		os.Exit(1)
	}
}

func main() {
	validateArgs()

	n, _ := strconv.Atoi(os.Args[1])

	var bar string

	{
		var sb strings.Builder
		sb.WriteString("+")
		for i := 0; i < n; i++ {
			sb.WriteString("-")
		}
		sb.WriteString("+")
		for i := 0; i < n; i++ {
			sb.WriteString("-")
		}
		sb.WriteString("+")
		bar = sb.String()
	}

	var upper string

	{
		var sb strings.Builder

		for i := 0; i < n; i++ {
			sb.WriteString("|")

			for j := 0; j < n; j++ {
				if i == j {
					sb.WriteString(`\`)
				} else {
					sb.WriteString(" ")
				}
			}

			sb.WriteString("|")

			for j := 0; j < n; j++ {
				if i == (n - j - 1) {
					sb.WriteString(`/`)
				} else {
					sb.WriteString(" ")
				}
			}

			sb.WriteString("|")

      if i < n - 1 {
        sb.WriteString("\n")
      }
		}

		upper = sb.String()
	}

	var lower string

	{
		var sb strings.Builder

		for i := 0; i < n; i++ {
			sb.WriteString("|")

			for j := 0; j < n; j++ {
				if i == (n - j - 1) {
					sb.WriteString(`/`)
				} else {
					sb.WriteString(" ")
				}
			}

			sb.WriteString("|")

			for j := 0; j < n; j++ {
				if i == j {
					sb.WriteString(`\`)
				} else {
					sb.WriteString(" ")
				}
			}

			sb.WriteString("|")

      if i < n - 1 {
        sb.WriteString("\n")
      }
		}

		lower = sb.String()
	}

	fmt.Println(bar)
	fmt.Println(upper)
	fmt.Println(bar)
	fmt.Println(lower)
	fmt.Println(bar)

}
```

## That’s it!!

So far, we had seen that a lot of questions are quite pretty difficult for us and challenging to many competitors in the event. And of course, CreatorsGarten win back-to-back as they won last year, by the great performance of P’ Thai Pangsakulyanont. This was a great opportunity that I try something challenging for my career as I competed this hackathon, and I will never forget this party. Thank you for reading, hope you like this story and see you next blog.
