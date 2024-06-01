## Specific Implementation
## Arrays

### Declaring Arrays

Arrays are declared in Javascript similar to other modern languages, indicated by the square brackets - `[]`. ^099550

This example shows an array called `cars` being declared with three elements.

```jsx
let cars = ["Saab", "Volvo", "BMW"];
```

Arrays can also be declared “empty” and then adding elements later in code.

```jsx
let cars = [];
cars[0]= "Saab";
cars[1]= "Volvo";
cars[2]= "BMW";
```

<aside>
💁 Javascript handles arrays differently from other languages. They are **resizable**. This means that the code can add or remove elements, as can be seen in the example above.

</aside>

<aside>
💁 Javascript arrays can contain a mix of data types. For instance some elements can be integers, others can be strings.

</aside>

### Accessing Array Elements

Accessing array elements is again similar to other languages - using the index of the element you wish to access.

```jsx
let cars = ["Saab", "Volvo", "BMW"];
alert (cars[0]); // This will create a popup with the text - Saab.
cars[2] = "Kia"; // This will override BWM with Kia.
```

## Key Value Pair

Javascript does not natively support Key Value Pairs. However, Javascript can emulate the functionality of Key Value Pair through the use of **Objects**. Objects are beyond the scope of this course, however this will show how to implement this in Javascript.

This object, called pizza, has three keys - `topping`, `sauce` and `size` - and three associated values - `cheese`, `marinara` and `small`.

```jsx
const pizza = {
    topping: "cheese",
    sauce: "marinara",
    size: "small"
};
```

> The keys are to the left of the colon **`:`** and the values are to the right of it. Each key-value pair is a `property`. There are three properties in this example:
> 
> - The key **topping** has a value **“cheese”**.
> - The key **sauce** has a value **“marinara”**.
> - The key **size** has a value **“small”**.
> 
> Each property is separated by a comma. All of the properties are wrapped in curly braces.
> 
> This is the basic object syntax. But there are a few rules to keep in mind when creating JavaScript objects.
> 
> [https://www.freecodecamp.org/news/javascript-object-keys-tutorial-how-to-use-a-js-key-value-pair/](https://www.freecodecamp.org/news/javascript-object-keys-tutorial-how-to-use-a-js-key-value-pair/)
> 

### Accessing Keys and Values

Particular values are access through identifying the keys within square brackets.

Similar to arrays, the code can read and write to and from the item in a similar manner.

```jsx
const pizza = {
    topping: "cheese",
    sauce: "marinara",
    size: "small"
};
alert(pizza['topping']); // Dialog box appears showing cheese
pizza['topping'] = "cheese and olives";
alert(pizza['topping']); // Dialog box appears showing cheese and olives

```

# Practical Exercises

In this exercise you’ll create an array of 100 random numbers and then calculate the average of them, and display it to the user.

In the Software Development Fundamentals Course, create a new HTML called dataStructures.html and replace the contents with this starter code.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script>
        function dataCode() {

        }
    </script>
    <title>Data Structures Code</title>
</head>
<body>

<h1>Data Structures - Web Development</h1>

<p id="outputPosition"></p>

<form name="dataForm">
    <button onclick="dataCode()" type="button">Run Data Structures Code</button>
</form>

</body>
</html>
```

### Generating 100 Random Numbers

In dataCode(), declare an empty array called `randomValues` which will be used to store the 100 random numbers.

![Screen Shot 2022-02-27 at 9.43.44 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.43.44_pm.png)

- Code
    
    ```jsx
    let randomValues = [];
    ```
    

Write the for loop to iterate 100 times.

In this loop, `loopCounter` is the Loop Control Variable, and it is used in this case to limit the amount of times the loop iterates to 100. Each time the loop iterates, `loopCounter` is increased by 1 (`loopCounter++`). loopCounter will be used to access individual the index of the `randomValues` array.

![Screen Shot 2022-02-27 at 9.45.46 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.45.46_pm.png)

- Code
    
    ```jsx
    for (let loopCounter = 0; loopCounter<100; loopCounter++) {
                    
    }
    ```
    

Generate a random number out of 1000. To do this, Javascript uses the `Math.random()` function which generates a float (decimal value) between 0.0 and 1.0 (but will never be 1.0). To generate a value from 0 to 1000, the result of `Math.random()` is multiplied by 1000.

![Screen Shot 2022-02-27 at 9.49.56 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.49.56_pm.png)

- Code
    
    ```jsx
    let randomNumber = Math.random() * 1000;
    ```
    

Store the `randomNumber` into the `randomValues` array using the `loopCounter` as the index.

<aside>
💁 Technically, the variable randomNumber is not needed in the code. The code could be more efficient by combining the two lines into one : `randomValues[loopCounter] =`***`Math***.random() * 1000;` However this was done just to highlight the different stages.

</aside>

![Screen Shot 2022-02-27 at 9.52.34 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.52.34_pm.png)

- Code
    
    ```jsx
    randomValues[loopCounter] = randomNumber;
    ```
    

Test the code at this stage, before continuing to ensure that the code is generating the random numbers correctly. 

After the for loop, display the whole array to the user through an `alert()` command.

The numbers generated will be different each time, however it indicates that it is working correctly.

![Screen Shot 2022-02-27 at 9.54.23 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.54.23_pm.png)

- Code
    
    ```jsx
    alert(randomValues)
    ```
    

After testing it the code, the alert command can be commented out by putting two slashes in front of the line of code.

![Screen Shot 2022-02-27 at 9.57.06 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_9.57.06_pm.png)

### Calculating the average

To calculate the average of a set of numbers, you follow this equation.

$$
average = \frac{total sum}{number of items in set}
$$

To implement this in code, first you need to declare a variable to keep track of the running total of the values.

Call this variable `total`, and declare it after the loop generating the values.

![Screen Shot 2022-02-27 at 10.01.12 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_10.01.12_pm.png)

- Code
    
    ```jsx
    let total = 0;
    ```
    

Create another for loop to iterate 100 times over the array.

The for loop will be the same as the previous one, so you can copy the loop and remove the code in between the brackets as shown.

![Screen Shot 2022-02-27 at 10.02.39 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_10.02.39_pm.png)

- Code
    
    ```jsx
    for (let loopCounter = 0; loopCounter<100; loopCounter++) {
                    
    }
    ```
    

Adding all the values together is done by adding `total` to the value stored in the particular index of the array and storing the result back into the `total` variable.

At the end of this loop, `total` will contain a value which is all the random numbers added together.

![Screen Shot 2022-02-27 at 10.04.27 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_10.04.27_pm.png)

- Code
    
    ```jsx
    total = total + randomValues[loopCounter];
    ```
    

Finally, to calculate the average, divide the `total` by the number of values, which is 100.

Additionally, output the average variable to the user through an `alert()` command.

![Screen Shot 2022-02-27 at 10.09.15 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_10.09.15_pm.png)

![Screen Shot 2022-02-27 at 10.08.40 pm.png](Notionimp/images/Screen_Shot_2022-02-27_at_10.08.40_pm.png)

- Code
    
    ```jsx
    let average = total / 100;
    alert(average);
    ```
    

# Review

1. **Practical**. Update the Array code calculating the Average, to output the answer to only 2 decimal places.
2. **Practical.** Create a new file, with the same starter code above, although this time, generate a Key Value Pair called `userDetails` to store the following keys. The values for each key can be collected from the user through prompt() commands. E.g. prompt the user to enter their username and store it in `userDetails[”username”]` etc.
    1. Username
    2. Password
    3. Full Name
    4. Email Address.
    - Answer
        
        ```jsx
        function dataCode() {
            let userDetails = {
                userName: "dummy username",
                password: "dummy password",
                fullName: "dummy fullname",
                email: "dummy email"
            }
        
            userDetails["userName"] = prompt("What is your username?");
            userDetails["password"] = prompt("What is your password?");
            userDetails["fullName"] = prompt("What is your Name?");
            userDetails["email"] = prompt("What is your email address?");
        
            var details = userDetails["userName"] + " " + userDetails["password"] + " " + userDetails["fullName"] + " " + userDetails["email"];
            alert(details);
        }
        ```
        
3. What situations would you choose a Key Value Pair over an array in JavaScript?
4. Which takes up more space in memory - Arrays or Dictionaries?

[Key Terms](Key%20Terms%205882f8a9faf74fd0919035b8414e69a5.csv)