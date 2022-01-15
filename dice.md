# **Creating a simple dice app with python**

**Project description:** This simple dice app allows users to decide the number of sides on the die.
Topics covered: functions, data types (string and integer), assigning variables, user inputs, if/else statements, print statements, while loops, imports.

## **Version 1 - Using IF/ELSE**

Relevant code snippets are uncommented for each step. The finished code: 

```python
import random

def dice_roll():
    sides = int(input('Input the number of sides on your die: '))
    roll = random.randint(1, sides)
    print('You rolled a', roll)   
    roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    if roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        return dice_roll()
    else: 
        print('Thanks for playing!') 
  
dice_roll()
```
### 1. Import random

Python has an extensive library of useful packages that we can import. One such example is random which will be used to generate random numbers to simulate the probabilistic nature of a die.

```python
import random
```
### 2. Define a function

Give the function a useful and memorable name that relates to what it does when used. As we are creating a dice rolling app, dice_roll has been suitably chosen as the function name.

Function structure >> **def the_function_name():**

```python
#import random

def dice_roll():
```

### 3. Assign variables

Now we want to start making our function useful.

We must now declare and assign variables within our function or, in other words, create the building blocks of the function. When thinking of dice, we need some way to represent the number of sides and an ability to roll. Therefore we will create 2 variables called sides and roll.

```python
#import random

#def dice_roll():
     sides = int(input('Input the number of sides on your die: ')) 
     roll = random.randint(1, sides)
```

*sides explained*
We want the sides to be an int (integer) data type because we want the sides to be in whole numbers. We also want the user to be able to choose the number of sides, for this we use the **input() function** which is a function that comes pre-installed with python. Within the input() function we enter the text we want our user to see: 'Input the number of sides on your die: '.

Numerical input structure >> **the_variable = int(input('The message you want your user to see: '))**

*roll explained*
We want the rolls to be generated randomly to reflect the probabilistic nature of a die so now we use the random function. We use randint (from random import) because we want whole numbers to be generated. Instead of a fixed value, the sides variable we created will act as the upper limit for the random numbers generated. This means that the number the user writes will become the maximum number the dice can return.

Generate random integer structure >> **the_variable = random.randint(minimum_value, maximum_value)**

### 4. Write the print statement

We add a print statement so that the user can actually see the number the dice app generated. To do this we use the print() function. The user will see the text written in the print statement followed by the roll (the randomly generated number).

Print statement with variable structure >> print('The text you want the user to see', a_variable)

```python
#import random

#def dice_roll():
    #sides = int(input('Input the number of sides on your die: '))
    #roll = random.randint(1, sides)
    print('You rolled a', roll)
```

### 5. Create option to roll again with user input. Write the IF/ELSE statement.

```python
#import random

#def dice_roll():
#    sides = int(input('Input the number of sides on your die: '))
#    roll = random.randint(1, sides)
#    print('You rolled a', roll)   
    roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    if roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        return dice_roll()
    else: 
        print('Thanks for playing!')
```
*roll_again explained*
This time we want the user input to be a str (string) data type because the user will be answering with letters or words. Within the input() function we enter the message and instructions we want our user to see: 'Would you like to roll again? Please enter Y or N to continue: '.

Text input structure >> **the_variable = str(input('The text you want your user to see: '))**

*if/else explained*
Because we have asked the user for a response, we now want our code to do something with it. One way is with an if/else statement.

We tell the program **if** something happens do this **else** do something else. In our case the something happens refers to what the user writes as their response, the do this refers to making the dice app ask the user to choose the sides on their die again, the something else refers to ending the dice app.

In the IF statement, lots of options for yes have been provided so that the user can write any variation of yes and continue rolling. Generally this is not best practice as an IF statement should capture the action without over-reliance on **and statements** or **or statements**. One option would be to use .lower() at the end of the input so that lowercase answers are accepted.

IF/ELSE structure >>
**if a_condition_to_be_met = a_value_of_the_condition:**
    **return an_action**
**else:**
    **return a_different_action**


### 6. Invoke the function

To run our code we must now invoke the function.

This means referencing the function somewhere else in the code (anywhere outside the function itself). It is important not to forget the () as the code will not run without them.

Invoke a function structure >> **the_function(function arguments, if any)**

```python
#import random

#def dice_roll():
    #sides = int(input('Input the number of sides on your die: '))
    #roll = random.randint(1, sides)
    #print('You rolled a', roll)   
    #roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    #if roll_again == 'Y' or roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        #return dice_roll()
    #else: 
        #print('Thanks for playing!') 
  
dice_roll()
```

## **Version 2 - Using WHILE loop**

The finished code:

```python
import random

def dice_roll():
    sides = int(input('Input the number of sides on your die: '))
    roll = random.randint(1, sides)
    print('You rolled a', roll)   
    roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    while roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        return dice_roll()
    print('Thanks for playing!') 
  
dice_roll()
```
### 1. Follow Steps 1 through 4 from Version 1 - Using IF/ELSE

```python
import random

def dice_roll():
    sides = int(input('Input the number of sides on your die: '))
    roll = random.randint(1, sides)
    print('You rolled a', roll)
```

### 2. Create option to roll again with user input and the WHILE loop.

Using the same method as Version 1, add a user input option that asks if they want to roll again.

```python
#import random

#def dice_roll():
    #sides = int(input('Input the number of sides on your die: '))
    #roll = random.randint(1, sides)
    #print('You rolled a', roll)   
    roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    while roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        return dice_roll()
    print('Thanks for playing!')
```
*while explained*
Another way we can get our code to do something in response to the user input is through a while loop.

We tell the program that while something is happening do this otherwise do something else and end the loop. In this case the something is happening refers to what the user writes as their response i.e. as long as the user responds with one of the accepted responses to continue rolling, the dice app will continue to run from beginnning to end. The do something else and end the loop refers to making the dice app print 'Thanks for playing!'and to stop running the dice app.

> Caution: It is possible to create infinite loops when using while if you are not careful enough to define a way for the loop to stop. To avoid this, break can be used to force the program to stop. Simply write break wherever you want a program to end.

WHILE LOOP structure >>
**while a_condition_to_be_met = a_value_of_the_condition:**
    **return an_action**
**return a_different_action**

## **Stretch Version - Importing the dice as an application**

### 1. Create a dice.py file

The function will be identical to the WHILE loop example in Version 2 except that this time, the function will not be invoked in the same file. Instead a separate file that is solely dedicated to running the dice app is created. In this sense, the dice.py file acts as a backend containing all the 'hidden' logic for the dice application.

```python
# dice.py file
import random

def dice_roll():
    sides = int(input('Input the number of sides on your die: '))
    roll = random.randint(1, sides)
    print('You rolled a', roll)   
    roll_again = str(input('Would you like to roll again? Please enter Y or N to continue: '))
    while roll_again == 'Y' or roll_again == 'y' or roll_again == 'yes'  or roll_again == 'YES':
        return dice_roll(sides)
    print('Thanks for playing!')
```

### 2. Create an application file (recommended name: dice_app.py)

Now that the backend logic has been handled elsewhere, we must import it (just like we did with random in Version 1) to be able to connect the front with the back and run the app. When we invoke the function, this time we must also reference the file containing the logic (dice).

Invoke a function that references a file structure >> **the_file.the_function(function arguments, if any)**

```python
# dice_app.py file
import dice

dice.dice_roll()
```
## This project is:

<img src="assets/images/python-power-logo-140x182.png"/>

### Congratulations! You have reached the end of this tutorial.

Hopefully you have been able to find something useful today. Remember, there are many different paths to a solution so don't feel that what you have seen today is the only way.

**Experiment, Stay Motivated and Keep Coding!**
