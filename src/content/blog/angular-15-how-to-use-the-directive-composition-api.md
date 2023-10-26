---
title: "Creating scalable parameterized functions"
description: "How to create scalable function that uses many parameters"
pubDatetime: 2023-10-26T20:40:00.000Z
tags:
  - javascript
  - typescript
  - refactoring
draft: false
feature: false
ogImage: "@assets/images/creating-scalable-parameterized-functions.png"
---

![creating-scalable-parameterized-functions.png](@assets/images/creating-scalable-parameterized-functions.png)

Functions with many parameters are difficult to use and understand. In this post, I want to show you how to refactor this kind of function in a more simple and scalable way.

## Table of contents

## Ugly function signature

As an example, I will use the following function:

```js
function myFunction(value, option1, option2, option3) {
  // do something
}


myFunction(30, null null, 'errorMessage');
```

> In this case `null` values mean that the parameter should be ignored for the function.

I remember that kind of function being very common in the JQuery age. Maybe because JavaScript was never so used as nowadays.

Notice that the parameters' function are difficult to understand. I would need to open the function code to see what each parameter is supposed to do.

I will refactor it in a more readable way.

## Refactoring the ugly function signature

Generally, a function should expect just one or two essential parameters (generally just one).

In the case of the `myFunction` function, the essential parameter is `value`. The other parameters are just options that will be used to customize the behavior of the function.

Well, I will use an object as a second parameter to set the option values that the function accepts.

```js
function myFunction(value, { option1, option2, option3 }) {
  // do something
}

myFunction(30, { option3: "errorMessage" });
```

Now, I do not need to pass `null` values to the function when I want the parameter to be ignored. Instead, I just pass an object with the option values that the function should use.

## Typed way

TypeScript is great for defining functions like that. I will refactor `myFunction` to use TypeScript interfaces.

```ts
interface MyFunctionProps {
  option1: boolean;
  option2: boolean;
  option3: string;
}

function myFunction(
  value: number,
  { option1, option2, option3 }: MyFunctionProps
) {
  // do something
}

myFunction(30, { option3: "errorMessage" });
```

Interfaces match very well with this kind of function.

## Thank you!

Thank you for reading up to this point, and I hope this article is as useful to you as it is to me.

Until the next time!
