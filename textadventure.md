---
layout: default
title: Text Based Adventure Game
description: This game allows users to make choices that affect their game ending.
---

**Topics covered:** functions, data types (string and integer), assigning variables, user inputs, if/else statements, print statements, while loops, imports.  

```python
import sys
import os
import random
import time

# Function for resetting console
def reset_console():
    print("\n")
    os.system('cls||clear')

def start_up(str, delay = 0.05): #Function to display start up text more slowly. Delay each letter 0.05s
    for i in str:
        sys.stdout.write(i)
        sys.stdout.flush()
        time.sleep(delay)
    print("\n")

def start_up_logo():
    print("  ____    __    _  _  ____  ___  _   _  ____  ____     ___  ____   ___  ____  ____  ____  ___") 
    print("'(  _ \  /__\  ( \( )(_  _)/ __)( )_( )( ___)(  _ \   / __)( ___) / __)(  _ \( ___)(_  _)/ __)'")
    print("  ) _ < /(__)\  )  (  _)(_ \__ \ ) _ (  )__)  )(_) )  \__ \ )__) ( (__  )   / )__)   )(  \__ \ ")
    print("'(____/(__)(__)(_)\_)(____)(___/(_) (_)(____)(____/   (___/(____) \___)(_)\_)(____) (__) (___/'")
    print("\n")

start_up_logo()
start_up("Banished Secrets Text Adventure Game 2021")

# Create functions for managing how text is displayed

def fprint(str, delay = 0): # When called pass in str and delay as the 2 arguments, allows for custom delays
    print("\n" + str)
    time.sleep(delay)

def sprint(str, delay = 0): # Same as the fprint but without the add newline formatting
    print(str)
    time.sleep(delay)

def kill():
    fprint("You died!", 0.5)

def won_game():
    fprint("You're a winner baby!", 0.5)    

# Create functions for each "room" in the game

def room_builder(room_list, room_name, end_room, next_rooms):
    delay = 0.5
    print(f"You are in the {room_name}.")
    time.sleep(delay)
    room_count = len(room_list)
    responses = []
    input_msg = "Choose a door: ("
    door_msg = ""
    
    for count in range(room_count):
        responses.append(f"door {count + 1}")
        if count + 1 < room_count: 
            door_msg += f"door {count + 1}, "
        else: 
            door_msg += f"door {count + 1})"

    input_msg += door_msg
    #print(input_msg)

    while True:
        choice = input(input_msg).lower()
        if choice in responses:
            if room_list[responses.index(choice)]:
                if end_room:
                    fprint("You made it to the end!", 0.5)
                    won_game()
                    break
                else:
                    fprint("Please proceed to the next room.", 0.5)
                    eval(next_rooms[responses.index(choice)] + "()")
                    break
            else:
                kill()
                break
        else: 
            time.sleep(delay)
            print(f"Invalid selection, you must choose ({door_msg}")


def kitchen(): 
    room_builder([True, True, True, True], "Kitchen", False, ["cellar", "bedroom", "garden", "secret_dungeon"])

def cellar():
    room_builder([False, True], "Cellar", False, ["kill", "garden"]) 

def bedroom():
    room_builder([True, True, False, True, True], "Bedroom", False, ["kitchen", "cellar", "kill", "garden", "secret_dungeon"])

def secret_dungeon():
    room_builder([True, False], "Secret Dungeon", True, ["won_game", "kill"])

def garden():
   room_builder([True, True, True], "Garden", False, ["kitchen", "cellar", "bedroom"])
# Create functions with lists for tracking steps travelled
# def steps():
    
#     steps_made_up = []
#     steps_made_down = []
#     steps_made_left = []
#     steps_made_right = []
    
#     for i in range(1):
#         steps_made_up.append(int(input("How many steps up will you walk?\n")))
#     for i in range(1):
#         steps_made_down.append(int(input("How many steps down will you walk?\n")))    
#     for i in range(1):
#         steps_made_left.append(int(input("How many steps left will you walk?\n")))
#     for i in range(1):
#         steps_made_right.append(int(input("How many steps right will you walk?\n")))  
    
#     print(steps_made_up)
#     print(steps_made_down)
#     print(steps_made_left)
#     print(steps_made_right)
    
#     total_steps = sum(steps_made_up)+sum(steps_made_down)+sum(steps_made_left)+sum(steps_made_right)
#     return total_steps

#Looped response inputs where player makes choices
while True:
    response = input("Do you want to play Banished Secrets? (yes/no) ")
    if response.lower().strip() == "yes":
        
        room_builder([True, True, True, True, True], "Main Hall", False, ["kitchen", "cellar", "bedroom", "garden", "secret_dungeon"])    
    else:
        print("Maybe another time then...")
        break
```

## This project is:

<img src="assets/images/python-power-logo-140x182.png"/>

### **Congratulations! You have reached the end of this tutorial.**

Hopefully you have been able to find something useful today. Remember, there are many different paths to a solution so don't feel that what you have seen today is the only way.

**Experiment, Stay Motivated and Keep Coding!**
