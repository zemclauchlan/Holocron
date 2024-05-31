# Specific Implementation

# Practical Exercises

In your Software Development Fundamentals project, create a new HTML5 file called `operations.html`.

![Screen Shot 2022-02-04 at 9.32.32 pm.png](Notionimp/images/Screen_Shot_2022-02-04_at_9.32.32_pm.png)

Replace the contents of this file with:

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>Mathematical & Logic Operations - Web Development</h1>

<form name='loginForm'>
    <b>Login Page</b>
    <p>
        Username:<input type='text' size=25 name='userid'><br>
        Password:<input type='Password' size=25 name='pwd'><br>
        <input type='submit' onclick='check(this.form)' value='Login'>
    </p>
</form>
<script>
    function check(form) {
        if (<!-- Update this condition -->) {
            window.open('README.md')
        } else {
            alert('Error Password or Username')/*displays error message*/
        }
    }
</script>

</body>
</html>
```

## Username and Password

This requirements for this page is that the username and password entered in the form are checked and confirmed to be correct before proceeding. If either of the username or password data is incorrect, and error will be displayed to the user. 

<aside>
💁 With the form already configured, the only section that needs to be updated is the `if` statement. `if` statements are covered in a later section, however the condition needs to be added.

</aside>

Both the username and the password need to be correct for the page to load the [README.md](http://README.md) file. If either or both of the two inputs are incorrect, then an error will be displayed. **What logic gate/truth table/logic operator is required?**

The answer is `AND` as both sides of the AND need to be true for the result to be true.

<aside>
💁 The operator for `AND` in Javascript is `&&`.

</aside>

Replace  `<!-- Update this condition -->` with `form.userid.value == 'admin' && form.pwd.value == 'admin'`. 

Run the page and see the output.

### Correct Username and password

![2022-02-04 21-45-06.2022-02-04 21_45_47.gif](loginCorrect.gif)

### Incorrect Username and password

![2022-02-04 21-45-52.2022-02-04 21_46_22.gif](loginIncorrect.gif)

## Input Validation

Ensuring the data that is entered by the user is called Input Validation.

Create a new file called `inputValidation.html`. Replace the contents with: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Input Validation</title>
</head>
<body>

<p>Please input a number between 1 and 10:</p>
<form>
    <input id="inputNumber" type="text">
    <button type="button" onclick="myFunction()">Submit</button>
    <p id="result"></p>
</form>
<script>
    function myFunction() {
        var x, text;
        //Get the value of input field with id="numb"
        x = document.getElementById("inputNumber").value;
        // If x is Not a Number or less than one or greater than 10
        if (<!-- Update this condition -->) {
            text = "Input not valid";
        } else {
            text = "Input OK";
        }
        document.getElementById("result").innerHTML = text;
    }
</script>

</body>
</html>
```

The requirements for this script is that the code will check the number entered. If the number not one of the following - 1, 2, 3, 4, 5, 6, 7, 8, 9, or 10, the output will be “Input not valid”. If the number entered is one of those 10 options, it will output “Input OK”. **What logic gate/truth table/logic operator is required?**

You could use an OR operator for this task. 

If the number is less than 1 OR the number is greater than 10, OR not a number at all, then output “Input not valid”, otherwise output “Input OK”.

<aside>
💁 The operator for `OR` in Javascript is `||`

</aside>

<aside>
💁 There’s always a number of approaches to code problems such as this. You could write code to individually check if the number entered is 1, then if it’s 2 etc. Not the most efficient, but it still would satisfy the requirements.

</aside>

Replace `<!-- Update this condition -->` with `isNaN(x) || x < 1 || x > 10`. This If statement has 3 different comparisons to check, with two OR operators between them. This is perfectly valid in most programming languages.

## Review

Discussion: Why is logic important when learning software development?

Discussion: What is the purpose of Karnaugh Maps and how does it assist us in developing solutions?

1. Go to [https://learn.electronics-course.com](https://learn.electronics-course.com/) (sign in with your school Google Account to save your progress) and complete the following projects:
    1. NAND Gate
    2. Half Adder
    3. Care Safety Buzzer

[Key Terms](Key%20Terms%207b7723beb3a04505b53b91ca8936de04.csv)