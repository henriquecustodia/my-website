---
title: "Angular 15: Using The Directive Composition API"
description: >-
  The directive composition API is a new feature released in Angular 15. It
  allows us to reuse the directive's code with components and even other
  directives.
pubDatetime: 2022-11-02T11:00:00.000Z
postSlug: "angular-15:-using-the-directive-composition-api"
tags:
  - angular
draft: false
feature: false
ogImage: "@assets/images/lucas-kapla-wqlagv4_oys-unsplash.jpg"
canonicalURL: "https://www.henriquecustodia.dev/posts/angular-15:-using-the-directive-composition-api/"
---

![lucas-kapla-wqlagv4_oys-unsplash.jpg](@assets/images/lucas-kapla-wqlagv4_oys-unsplash.jpg)

Angular v15 will be released pretty soon, and it's coming with a very nice feature called **Directive Composition API**.

## Table of contents

## But, what is it? 🤔

The Directive Composition API allows us to compose directives into components and other directives.

This API works only with standalone components (and standalone directives). As the 14 version added the standalone property, the 15 version added a **hostDirectives** property.

Let's see how to use this property.

The example below shows a directive called **BoxDirective**, that sets some styles to the **AppComponent** using the **Composition API**:

![](@assets/images/raycast-untitled.png)

![](@assets/images/raycast-untitled-1.png)

The result will be:

![](@assets/images/result1.PNG)

We can use this new API to reuse a lot of code. It's amazing.

## Exposing the directive's input

When adding Inputs and Outputs to a directive, we need to expose those to the component to be able to use them. There are the **input** and **output** in the **hostDirectives** property because of it.

The following example adds an Input property to the BoxDirective.

![](@assets/images/raycast-untitled-2.png)

And we'll add the **color input** to the inputs array to expose it to the component.

![](@assets/images/raycast-untitled-3.png)

That way we can set a color to the **BoxDirective**

![](@assets/images/raycast-untitled-4.png)

The result will be:

![](@assets/images/result2.PNG)

It's possible to rename the exposed input's name - generally useful when we have directives' inputs with the same name.

![](@assets/images/raycast-untitled-5.png)

Using the renamed property:

![](@assets/images/raycast-untitled-6.png)

## Exposing the directive's output

To expose outputs as easily as with inputs. But there's a property called **outputs** specifically for it.

![](@assets/images/raycast-untitled-7.png)

![](@assets/images/raycast-untitled-8.png)

Using it

![](@assets/images/raycast-untitled-9.png)

In the same way as inputs, it's possible to rename the output's name.

![](@assets/images/raycast-untitled-10.png)

![](@assets/images/raycast-untitled-11.png)

## Bonus: OnDestroyDirective 💎

Let's create a reusable directive to destroy old subscriptions.

The following code creates a timer component that uses an interval operator to log an incremental number every second. To avoid memory leaks, it's a good practice to remove observable subscriptions when a component has been destroyed. The **OnDestroyDirective** will remove the interval subscription automatically after the timer component is destroyed.

![](@assets/images/raycast-untitled-12.png)

![](@assets/images/raycast-untitled-13.png)

The result will be:

![](@assets/images/2022-11-01-23-32-47.gif)

## 👨‍💻

You can check out the code of this post [here](https://stackblitz.com/edit/ng-15-directive-composition-api?file=README.md).

## That's all!

I've spent some time writing this post, then, I hope that you enjoyed it!

If you liked it, give some claps/likes to this post or share it with your friends!

Thank you for the reading. 😄

See you! 👋🏼
