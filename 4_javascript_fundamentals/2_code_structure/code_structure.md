# Code structure

The first thing we’ll study is the building blocks of code.

## Statements

Statements are syntax constructs and commands that perform actions. <br>
We’ve already seen a statement, `alert('Hello, world!')`, which shows the message “Hello, world!”. <br>
We can have as many statements in our code as we want. Statements can be separated with a semicolon. <br>
For example, here we split “Hello World” into two alerts:

`alert('Hello'); alert('World');`

Usually, statements are written on separate lines to make the code more readable:

```
alert('Hello');
alert('World');
```

## Semicolons

A semicolon may be omitted in most cases when a line break exists. <br>
This would also work:

```
alert('Hello')
alert('World')
```

Here, JavaScript interprets the line break as an “implicit” semicolon. This is called an automatic semicolon insertion. <br>
In most cases, a newline implies a semicolon. But “in most cases” does not mean “always”! <br>
There are cases when a newline does not mean a semicolon. For example:

```
alert(3 +
1
+ 2);
```

The code outputs 6 because JavaScript does not insert semicolons here. <br>
It is intuitively obvious that if the line ends with a plus "+", then it is an “incomplete expression”, so a semicolon there would be incorrect. <br>
And in this case, that works as intended.
But there are situations where JavaScript “fails” to assume a semicolon where it is really needed. <br>
Errors which occur in such cases are quite hard to find and fix. <br>

An example of an error
If you’re curious to see a concrete example of such an error, check this code out:

```
alert("Hello");

[1, 2].forEach(alert);
```

No need to think about the meaning of the brackets `[]` and `forEach` yet. We’ll study them later. For now, just remember the result of running the code: it shows `Hello`, then `1`, then `2`.

Now let’s remove the semicolon after the alert:

```
alert("Hello")

[1, 2].forEach(alert);
```

The difference compared to the code above is only one character: the semicolon at the end of the first line is gone. <br>
If we run this code, only the first `Hello` shows (and there’s a TypeError, you may need to open the console to see it). There are no numbers any more. <br>
That’s because JavaScript does not assume a semicolon before square brackets `[...]`. <br>
So, the code in the last example is treated as a single statement.

Here’s how the engine sees it:

`alert("Hello")[1, 2].forEach(alert);`

Looks weird, right? Such merging in this case is just wrong. We need to put a semicolon after `alert` for the code to work correctly. <br>
This can happen in other situations also.

We recommend putting semicolons between statements even if they are separated by newlines. <br>
This rule is widely adopted by the community. <br>
Let’s note once again – it is possible to leave out semicolons most of the time. <br>
But it’s safer to use them to prevent errors.

## Comments

As time goes on, programs become more and more complex. It becomes necessary to add *comments* which describe what the code does and why. <br>
Comments can be put into any place of a script. They don’t affect its execution because the engine simply ignores them. <br>

**One-line comments start with two forward slash characters `//`.**

The rest of the line is a comment. It may occupy a full line of its own or follow a statement. <br>
Like here:

```
// This comment occupies a line of its own
alert('Hello');
```

`alert('World'); // This comment follows the statement`

**Multiline comments start with a forward slash and an asterisk `/*` and end with an asterisk and a forward slash `*/`.** <br>
Like this:

```
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

The content of comments is ignored, so if we put code inside `/* … */`, it won’t execute. <br>
Sometimes it can be handy to temporarily disable a part of code:

```
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

### Use hotkeys! <br>
In most editors, a line of code can be commented out by pressing the `Cmd+/` hotkey for a single-line comment and something like `Option+Shift+A` – for multiline comments (select a piece of code and press the hotkey).

### Nested comments are not supported! <br>
There may not be `/*...*/` inside another `/*...*/`.

Such code will die with an error:

```
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```

Please, don’t hesitate to comment your code.

Comments increase the overall code footprint, but that’s not a problem at all. There are many tools which minify code before publishing to a production server. <br>
They remove comments, so they don’t appear in the working scripts. <br>
Therefore, comments do not have negative effects on production at all.

Later there will be a chapter code quality that also explains how to write better comments.