---
title: "Booleans"
date: 2019-07-23T11:45:38-07:00
draft: false
weight: 8
---

## Booleans

**Booleans** are `true` or `false` statements. Unlike strings or numbers, booleans store statements of truth: is what I am saying true or false? For example, if I ask, "Are you a robot?", this question produces a `true` or `false` result, which we call a **Boolean**. In this case, since you are not a robot (hopefully!), we would produce `false`.

We can also use math operators to create boolean expressions. Here are some examples; however, notice the unusual symbols for "equal to" and "not equal to":

| Operator | Description           | Operator | Description              |
| -------- | --------------------- | -------- | ------------------------ |
| `<`      | Less than             | `>`      | Greater than             |
| `<=`     | Less than or equal to | `>=`     | Greater than or equal to |
| `==`     | Equal to              | `!=`     | Not equal to             |

As usual, use `Console.WriteLine` to print out your results:

```csharp
Console.WriteLine(10 < 8);
Console.WriteLine((3 * 6) == (32 - 14));
```

![alt text height="600px" width="70%"](../media/booleans-intro.png "Printing booleans")

{{% notice tip %}}

## Working Together

Try guessing the answers to the following expressions. Use `Console.WriteLine` to check your answers.

- `54 < (10 + 32)`
- `(37 / 5) == 7`
- `"Hello" + "World" == "Hello World"`
- `false == false`

<iframe width="100%" height="475" src="https://dotnetfiddle.net/Widget/ULv0JH" frameborder="0"></iframe>

{{% /notice %}}
