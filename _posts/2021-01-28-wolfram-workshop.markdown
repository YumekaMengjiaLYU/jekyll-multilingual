---
layout: post
comments: true
title:  "Wolfram Workshop Series"
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


```wl
Manipulate [Plot[Sin[freq*x],{x,0,10}],{freq,1,10}]
```
Wolfram Demonstration Projects have lots of examples
```wl
data=Import["https://www.handsonstart.com/ExampleDataScores.txt","Data"]

Part[data,1]

Part[data, All, 3]

Histogram[%]

states = Import["ExampleData/50states.txt","Data"]

Interpreter["USState"][states]

Manipulate[Plot[amp*func[freq*x],{x,0,6Pi},PlotRange->4],{freq,1,5},{amp,1,4},{func,{Sin,Cos,Tan}}]

CloudDeploy[Manipulate[Plot[amp*func[freq*x],{x,0,6Pi},PlotRange->4],{freq,1,5},{amp,1,4},{func,{Sin,Cos,Tan}}]]

```


(Below is a summary of the  Columbia Data Science Society and Wolfram Research Workshop today.)
Wolfram Language, has a uniform structure, and **everything is an expression**.

1/2 is not the same as 0.5, construct-wise

the construction of function using aridic

+ FullForm
+ InputForm
+ TreeForm
a little shortcut
/@


```wl
Atomic expressions
5 
m
Select
1+7
"{1,2,3}"
Log[7.0] 


Set =
SetDelayed := makes it so that every time that var is called 

We can check what are the symbols that we as the user have created by using the Names function

remove the whole set of defined user symbols by using Remove

x=3;
y=x;
x=4;
y^2

output = 9

x=3;
y:=x;
x=4;
y^2

output =16

x=5;
f[x_]=x^2
f[2]

output =25




x=5;
f[x_]:=x^2
f[2]

output =4

Tally

+ Using the list {}, filter the list and remov ethe labels

Rest[{{"column 1","column 2","column 3"}, "}]
```

```wl
iteration
core to programming
would like to have machine repeat things

For[start,test,incr,body]

For[i=0,i<10,]

While[test,body]


=== represents true equality

Red === RGBColor[1,0,0]

Table
a very common iterator

compared to a for loop, creating the same matrix is much easire to do using Table
Do is another main iterator
does not produce an output

Map
apply a function to a list of elements

if you are interested in seeing the whole list you can use the nestlist operation

Exercises
+ 
Table[1,5,5]

Table[i^3, {i,10}]


Graphics[Circle[{0,0},1]]

Graphics[Table[Circle[{0,0},r]],{r,1,5}]

association
creation of rules

/.replace

The converse operation is the Normal function

Map

KeyMap


Exercises
1.

Association[{"Blue"->blue, "Red"->Red,"Green"->Gree}]

2.
AssociationMap[Prime, Range[10]]

Flow Control

Conditionals

One of the most common use of flow controls is the if operator

If[condition, t]

which is a nice way of implementing an else if statement

the Wolfram Language code is also data

SetDelayed for Functions
f[x_]:=x^2+3

Strings are atomic elements
StringMatchQ
StringFreeQ
StringCases

Exercises
1.
{f[],f[a],f[b,c],f[d,e,f]} /.f[x___]:>g[x]

<> string join

3. starting with the following input, create a list plot of 10 random real numbers

ListLinePlot RandomReal[10,10]

great for simulation
```

[Part 2 Presentation][ref-1]

[ref-1]:https://www.wolframcloud.com/obj/dstevens/Published/CDSS_Day1_Part2.nb









