# Specific Implementation

## IF..THEN..

Javascript uses the ‘standard’ C syntax for `if .. then` blocks. 

```jsx
if (condition) {
    ...
}
```

<aside>
💁 Important to note - the comparison inside the brackets, which determines in the IF statement is true or not is called the **condition.**

</aside>

### IF..THEN.. Example

In this example the variable `username` is checked to see the contents are the string `admin`. If that is correct, then the block of code within the `{}` is executed, in this case, opening the `user.html`.

In this example, if the `username` is not `admin`, then nothing occurs and the block is skipped.

<aside>
💁 Note the `==`. In Javascript, this is checking **equality**. A single `=` is an assignment statement.

</aside>

```jsx
if (username == 'admin') {
    window.open('user.html')
}
```

## IF..THEN.. ELSE..

The standard IF..THEN structure can be extended with an ELSE to allow a code block to run if the condition is false.

```jsx
if (condition) {
    ...
} else {
    ...
}
```

### IF..THEN..ELSE.. Example

An extension of the previous example, this shows that if the condition is false (in this case is `username` is **not** admin), then the else code block is executed, opening `loginError.html`.

```jsx
if (username == 'admin') {
    window.open('user.html')
} else {
        window.open('loginError.html')
}
```

## Switch ... Case

Switch cases are a different type of control structure to replace multiple, nested if..then statements. 

Based on a given variable, Javascript code can have multiple cases or a catch-all state - default. They can be used to simplify code, but still provide multiple cases for a variables.

### Syntax

```jsx
switch(expression) {
    case x:
    // code block
    break;
    case y:
    // code block
    break;
    default:
    // code block
}
```

### Example

```jsx
var text;
var fruits = document.getElementById("myInput").value;

switch(fruits) {
    case "Banana":
    text = "Banana is good!";
    break;
    case "Orange":
    text = "I am not a fan of orange.";
    break;
    case "Apple":
    text = "How you like them apples?";
    break;
    default:
    text = "I have never heard of that fruit...";
}
```

## **Comparison Operators**

The standard *comparison* operators in Javascript are shown here and can be used in `if` conditions.

| Operator | Description |
| --- | --- |
| ! | Not |
| x == y | x is equal to y |
| x != y | x is not equal to y |
| x < y | x is less than y |
| x > y | x is greater than y |
| x <= y | x is less than or equal to y |
| x >= y | x is greater than or equal to y |

## Logical Operators

| Operator | Description | Example |
| --- | --- | --- |
| && | AND  | form.userid.value == 'admin' && form.pwd.value == 'admin’ |
| || | OR | form.answer.value == "11111111” || form.answer.value == "FF” |
| ! | NOT | !(form.userid.value == 'admin') |

# Practical Exercises

Create a new file in the Software Development Fundamentals Project called `decisions.html`.

Replace the contents with the code shown.

This page will be used to ask 2 maths based questions. The code will run when the user presses the button, and will check the answers given in the Javascript if statements.

If each answer is correct, the page will show “Correct!” next to the answer.

If the answer is incorrect, the page will show “Incorrect!” instead.

Check the page loads correctly before continuing.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script>
        function checkMaths(form) {
            
        }
    </script>
</head>
<body>

<h1>Decisions - Web Development</h1>

<form name='mathsForm'>
    <b>Maths Quiz!</b>
    <p>
        <label>What is 2 to the power of 10?</label>
        <input type='text' size=25 name='answerPower'>
        <label id="powerOutput"></label>
    </p>
    <p>
        <label>What is the binary equivalent to the decimal number 255?</label>
        <input type='text' size=25 name='answerBinary'>
        <label id="binaryOutput"></label>
    </p>
    <button onclick="checkMaths(this.form)" type="button"> Check Maths</button>
</form>

</body>
</html>
```

In the checkMaths() function, add the following If statement.

This will look at the input the user entered in the `answerPower` field and compare it to `1024`. If that’s what the user entered, it will change the `label` with the ID `powerOutput` to `Correct!`

```jsx
if (form.answerPower.value == "1024") {
    document.getElementById("powerOutput").innerHTML = "Correct!";
}
```

![Screen Shot 2022-02-13 at 10.28.36 pm.png](Notionimp/images/Screen_Shot_2022-02-13_at_10.28.36_pm.png)

Now to include the else clause, which will run if the value is **not** 1024.

```jsx
if (form.answerPower.value === "1024") {
    document.getElementById("powerOutput").innerHTML = "Correct!";
} else {
    document.getElementById("powerOutput").innerHTML = "Incorrect!";
}
```

![Screen Shot 2022-02-13 at 10.31.47 pm.png](Notionimp/images/Screen_Shot_2022-02-13_at_10.31.47_pm.png)

Test the page. Try entering correct and incorrect values.

Now include similar checks for the other question.

![Screen Shot 2022-02-13 at 10.33.03 pm.png](Notionimp/images/Screen_Shot_2022-02-13_at_10.33.03_pm.png)

Test the page. Try entering correct and incorrect values.

# Review

1. What is the difference between == and === in javascript?
2. Include another Maths or logic-based question. Check the answer given and output appropriately.
3. Write a question where there are two answers needed. For instance, what is 100 in binary and hexadecimal? The output is only `Correct!` if both inputs are correct. [Use this site](https://www.rapidtables.com/convert/number/decimal-to-hex.html) to confirm the correct answers.
4. Write the code necessary to ask users for their favourite movie/car/shoes etc (your choice). Write a switch statement to check for at least 3 different possible answers, as well as a `default` case.

[Key Terms](Key%20Terms%2037d4ad38f4d9477a9692607e2e95be2d.csv)