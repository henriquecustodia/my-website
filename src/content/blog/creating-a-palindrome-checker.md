---
title: "Creating a palindrome checker"
description: "Creating a function to check if a sentence is a palindrome"
pubDatetime: 2024-02-23T15:00:00-3
tags:
  - javascript
  - typescript
  - algorithm
draft: false
feature: false
ogImage: "@assets/images/creating-a-palindrome-checker.jpg"
---

![creating-a-palindrome-checker.jpg](@assets/images/creating-a-palindrome-checker.jpg)

Recently, I was asked to create a function to check if a sentence is a palindrome.

And well, I confess that I struggled a little bit to solve the problem. I've never really made a function like that and I even didn't know what was a palindrome.

Then, if you're wondering in this moment what's it, here's a complete description of it.

## What's a palindrome?

A palindrome is a word, phrase, number, or other sequence of characters that reads the same forward and backward, ignoring spaces, punctuation, and capitalization.

In other words, a palindrome retains its meaning even when its characters are reversed.

Some examples of palindromic words are "radar," "level," "deified," and "civic."

Palindromic phrases include "A man, a plan, a canal, Panama!" and "Madam, in Eden, I'm Adam."

Palindromic numbers are those that remain the same when their digits are reversed, such as 121, 1331, and 12321.

Palindromes are often used for wordplay, puzzles, and linguistic curiosity.

## The palindrome function

After this brief explanation of what's a palindrome, here's how the function to check it can be done.

```ts
const toLowerCase = (word: string) => word.toLocaleLowerCase();
const removeWhitespaces = (word: string) => word.replace(/ /g, "");
const toArray = (word: string) => word.split("");

export function isPalindrome(word: string): boolean {
  const wordAsArray = toArray(removeWhitespaces(toLowerCase(word)));

  const middleIndex = Math.floor(wordAsArray.length / 2) - 1;

  let start = 0;
  let end = wordAsArray.length - 1;

  while (start <= middleIndex) {
    if (wordAsArray[start] !== wordAsArray[end]) {
      return false;
    }

    start += 1;
    end -= 1;
  }

  return true;
}
```

## Explaining the code

I don't think I need to explain every single line of the code above, but it's important to highlight some important things about.

First of all, you need to transform every character to lowercase.

```ts
const toLowerCase = (word: string) => word.toLocaleLowerCase();
```

You need remove all the whitespace of the string to have sure that all the compared characters will be always letters and not spaces.

```ts
const removeWhitespaces = (word: string) => word.replace(/ /g, "");
```

After that you need to convert the string to an array.

```ts
const toArray = (word: string) => word.split("");
```

> Yeah, I know that you can just access every string's character by index directly, but I prefer to convert the string to an array because it's readable.

Now you can use everything at once.

```ts
const wordAsArray = toArray(removeWhitespaces(toLowerCase(word)));
```

The next step you'll need to find the middle of the array. That way you can check all the characters by looping the `wordAsArray` variable.

Let's start the array index that way:

```ts
let start = 0;
let end = wordAsArray.length - 1;
```

> Note that `end` variable starts at the end of the array.

Ok, now you can just start to check every position of the `wordAsArray`.

```ts
while (start <= middleIndex) {
  if (wordAsArray[start] !== wordAsArray[end]) {
    return false;
  }

  start += 1;
  end -= 1;
}
```

If a single character from the beginning and end of the `wordAsArray` be different you can return `false` instantly. It means that the sentence isn't a palindrome.

```ts
if (wordAsArray[start] !== wordAsArray[end]) {
  return false;
}
```

If it be equals, you can check the next character.

```ts
start += 1;
end -= 1;
```

When the `start` variable be greater than `middleIndex` variable, then the sentence has been all checkedand you can return `true` because the sentence is a palindrome.
