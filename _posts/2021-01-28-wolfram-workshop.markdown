---
layout: post
comments: true
title:  "Wolfram Workshop Series Day 1"
ref: welcome
date:   2021-01-28
tags: theory
lang: en
---

(Below is a summary of the  Columbia Data Science Society and Wolfram Research Workshop today.)


### Personal Points

Wolfram language is both a numerical and symbolic language.

Use the suggestion bar to show all digits of a calculation.



+ press equal: equal sign -> free form input (Can query using natural language )
for instance can type in: picture of a caffein molecule -> shift enter -> picture will be shown

+ press control + equal: natural language bubble : can see what Wolfram codes are being interpreted 



WikipediaData can pull up Wiki articles

Put semicolon at the end of a function can quiet the output

Can use the free form input and the Wolfram language together
+ for instance, type "image of albert einstein"
+ can use EdgeDetect[%] to run on the picture 
+ % calls out output from the last cell

### Rules of the Wolfram Language
+ All Wolfram Built-in functions begin with a capital letter

+ Function arguments are enclosed by square brackets eg.[]

+ Lists or range or domainas are enclosed in curly braces eg.{}

+ Shift-Enter to perform a calculation/Evaluate

### Multiple Calculations

### Interactive Models

Manipulate function

How frequency affects x

Manipulate [Plot[Sin[freq*x],{x,0,10}],{freq,1,10}]

Wolfram Demonstration Projects have lots of examples

data=Import["https://www.handsonstart.com/ExampleDataScores.txt","Data"]

Part[data,1]

Part[data, All, 3]

Histogram[%]

states = Import["ExampleData/50states.txt","Data"]

Interpreter["USState"][states]

Manipulate[Plot[amp*func[freq*x],{x,0,6Pi},PlotRange->4],{freq,1,5},{amp,1,4},{func,{Sin,Cos,Tan}}]

CloudDeploy[Manipulate[Plot[amp*func[freq*x],{x,0,6Pi},PlotRange->4],{freq,1,5},{amp,1,4},{func,{Sin,Cos,Tan}}]]

[Part 2 Presentation][ref-1]

[ref-1]:https://www.wolframcloud.com/obj/dstevens/Published/CDSS_Day1_Part2.nb






