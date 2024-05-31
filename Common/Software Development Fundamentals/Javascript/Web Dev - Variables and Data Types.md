# Specific Implementation

Unlike some other languages, Javascript is a loosely typed and dynamic language. This is similar to Python, GDScript and other languages.

Variables must be identified with unique names and must begin with a letter.

<aside>
💁 Dynamic typed means that variables can change their data types during code execution.

</aside>

<aside>
💁 Loosely typed means that the programmer doesn’t need to specify the data type of a variable.

</aside>

## Declaring variables

When declaring variables, you can use the `let` or `var` keywords. `let` is a more recent addition to the language, however if your code needs to run on older browsers, use `var`.

As the language is dynamic, there is no need to include the data type in the variable declaration. For example

![[https://developer.mozilla.org/en-US/docs/Web/JavascriptImages/Data_structures](variableDeclare.png)

[https://developer.mozilla.org/en-US/docs/Web/JavascriptImages/Data_structures](https://developer.mozilla.org/en-US/docs/Web/JavascriptImages/Data_structures)

## Javascript Data Types

In Javascript, there are a number of the standard primitive types. The syntax for each of these are:

| Data Type | Description | Possible Values |
| --- | --- | --- |
| Null | No value associated with the variable |  |
| IntegerNumber | Numbers between  | -(2^53 − 1) and 2^53 − 1. Can also be NaN - Not a Number. |
| Boolean | Two possible values. | true or false.  |
| String | Text data. Stored internally as an Array (more on that later). | "Lake Tuggeranong College"
"32" |


## Constants

When declaring constants in Javascript, use the const keyword *before* the variable declaration. When declaring a constant, a value must be set.

![Screen Shot 2022-01-25 at 10.06.49 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.06.49_pm.png)

# Practical Exercises

Open the Software Development Fundamentals - Web Development project in Webstorm. Right click on the project folder and choose New HTML file.

![Screen Shot 2022-01-25 at 10.21.15 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.21.15_pm.png)

Give the name of the file as “variables”.

![Screen Shot 2022-01-25 at 10.21.24 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.21.24_pm.png)

Replace the contents of the file with the following:

```html
<!DOCTYPE html>
<html>
<body>

<h1>Variables and Data Types - Web Development</h1>
<p>Variable Output</p>

<p id="simpleOutput"></p>

<script>
    document.getElementById("simpleOutput").innerHTML = 5 + 6;
</script>

</body>
</html>
```

![Screen Shot 2022-01-25 at 10.21.34 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.21.34_pm.png)

You can “run” the code by clicking on one of the buttons to open in a browser, or open it within Webstorms by clicking on the icon that appears as shown.

![Screen Shot 2022-01-25 at 10.25.38 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.25.38_pm.png)

The code is a relatively simple HTML file, which has a heading and some text, but importantly for our purposes is the section highlighted here.

This code is rendered by the browser, by creating an empty paragraph tag (<p>) and giving it an identifier of “simpleOutput”. In the following <script> </script> code, the code searches for the element with the id of “simpleOutput” and replaces its contents with the answer to the equation of 5+6.

This is important, because you can code the <script> </script> to display any information you wish by changing the data that is displayed, or by performing some calculation prior to output.

```html
<p id="simpleOutput"></p>
```javascript
<script>
document.getElementById("simpleOutput").innerHTML= 5 + 6;
</script>
```



## Calculate the Area of a Circle

The equation for calculating the area of a circle is $A = \pi r^2$. To calculate this in Javascript, you could update the Javascript code in the <script>..</script> block like so.\

```html
<script>
    const pi = 3.14159;
    radiusOfCircle = 5;
    areaOfCircle = pi * radiusOfCircle * radiusOfCircle;
    document.getElementById("simpleOutput").innerHTML = areaOfCircle;
</script>
```

![Screen Shot 2022-01-25 at 10.34.58 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.34.58_pm.png)

## Multiple Outputs

If you wish to have multiple outputs in your HTML file, you can add a new `<p>` tag with a different id.

```html
<p>Variable Output</p>
<p id="simpleOutput"></p>

<p>Area of a Circle</p>
<p id="areaOfACircle"></p>

<script>
	document.getElementById("simpleOutput").innerHTML= 5 + 6;

	const pi = 3.14159;
	radiusOfCircle = 5;
	areaOfCircle = pi * radiusOfCircle * radiusOfCircle;
	document.getElementById("areaOfACircle").innerHTML = areaOfCircle;
</script>
```




![Screen Shot 2022-01-25 at 10.48.24 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_10.48.24_pm.png)

# Review

1. How is data stored in memory?
2. What’s the difference between primitive and non-primitve data types?
3. What is type inference?
    1. Find three programming languages that use type inference.
4. What is the opposite of type inference?
    1. Find three programming languages that don’t use type inference.
5. What does strongly typed and weakly typed languages mean?
6. On the `variables.html` file, calculate the area of a square and output a heading and the result in a new `<p>` tag.
7. Create a constant, called `hoursInAWeek` and set it to `168`. Then create two variables, one called `hoursAtSchool` and the other `hoursAtWork`. Set `hoursAtSchool` to be 20 and `hoursAtWork` to be however many hours you work in an average week (or guesstimate). Output the percentage of the week that you’re:
    1. at school, and 
    2. at work.
8. Research “Javascript string concatenation” and code 3 string variables, concatenate them together to output. Make sure there are spaces in the output!

1. What would `x` be after this line of code? Why / how does that work? 

![Screen Shot 2022-01-25 at 11.16.29 pm.png](Notionimp/images/Screen_Shot_2022-01-25_at_11.16.29_pm.png)

1. Using variables to store your name, age, (fictional) address, write code to display a welcome message similar to - “Hello, my name is Ryan, I am at least 42 years old, and live at 123 Street St.”

[Key Terms