# From Zero to GUI Hero: Mastering Python and Guizero in 14 Epic Projects

## Contents
[Introduction](#intro)

[Install and Setup Guizero](#install)

[Project One: Hello GUI](#first)

[Project Two: Lost Cat Poster](#cat)

[Project Three: A Dice Game](#dice)

[Project Four: Username Generator](#interactive)

[Project Five: Create a meme generator](#meme)

[Project Six: Popups](#pop)

[Project Seven: Calculator App](#calc)

[Project Eight: Tic Tac Toe Game](#ttt)

[Project Nine: Emoji Match](#emoji)

[Project Ten: Paint App](#paint)

[Project Eleven: Interactive Game Menu](#menu)

[Project Twelve: Animated Countdown Timer](#timer)

[Project Thirteen: Interactive Storytelling App](#story)

[Project Fourteen: Virtual Pet Simulator](#pet)

[Summary](#summary)

[References](#ref)

## Introduction <a name="intro"></a>
By using a graphical user interface (GUI), or "gooey"), Python programs can be made more user-friendly and fascinating. With the help of the Guizero library, beginners can add several "widgets" to their user interfaces, giving the program a wide variety of input and output methods. It allows people to be able to select an item from a menu, press a button, or see some text on a screen.

![GUI Image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8iwsb775ycrn0bo2s8oz.gif)

## Install and Setup Guizero<a name="install"></a>
Python’s standard GUI package is called [tkinter][1], and is already installed with Python on most platforms. As a wrapper for tkinter, the guizero package provides a considerably more user-friendly interface for using the default GUI library for Python. 

You need to install Guizero to get it up and running. To install it, open your command line / terminal and input the command provided below.
```
pip3 install guizero
```
You can visit the [Github Page](https://github.com/lawsie/guizero) for detailed installation instructions.

## Project One: Hello GUI<a name="first"></a>

To create your first GUI app, open your code editor or Python IDE. After that, you'll need to import each widget; hence, you can use it as many times as you wish throughout your program. To import the App widget, select and import the widgets you need from the guizero library at the start of each guizero program using the following command. 
```python
from guizero import App
```
After that, enter the following code to create your first GUI app.
```python
app = App(title="Hello, world!")
app.display()
```
You can now save and run your code. A GUI window with the title "Hello, world!" should appear. 

Congrats!! You created your first GUI application.

## Project Two: Lost Cat <a name="cat"></a>
Click <a href="https://drive.google.com/file/d/1hCSQcVa-_eySAA9Mf_JOU7Cworf7b3c0/view?usp=share_link">here</a> to download the project files. 

```python
from guizero import App, Text, Picture

app = App("Wanted Cat", bg='pink')

picture = Picture(app, image="cat-133_128.gif")
message = Text(app, text='Help find my Cat', color='green', size=16, font='verdana')

app.display()

```
The creates a GUI window using the guizero library, displays a picture of a cat, and shows a text message below it. The background color of the app window is set to pink.

**Exercise:** Create a Birthday Card

## Project Three: Dice Roll Game <a name="dice"></a>

```python
from guizero import App, Box, Text, PushButton
import random

# App
app = App("Dice Rolling Game")

# Function to roll the dice
def roll_dice():
    dice_value = random.randint(1, 6)
    dice_text.value = str(dice_value)

# Create the dice box
dice_box = Box(app, layout="grid")

# Create the dice text
dice_text = Text(dice_box, text="Click to roll", size=40, grid=[0, 0, 2, 1])

# Create the roll button
roll_button = PushButton(dice_box, text="Roll", command=roll_dice, grid=[0, 1, 2, 1])

# Display the app
app.display()
```
The code is basic implementation of a dice rolling game using the guizero library. When the user clicks the "Roll" button, a random value between 1 and 6 is generated, and the value is displayed on the screen. 
If you'd like to expand the functionality of the dice rolling game, here are a few ideas:

- 
Add multiple dice: Modify the code to include multiple dice and display the individual values of each dice.

- 
Keep track of the total score: Create a variable to keep track of the total score and update it with each roll.

- 
Add animations: Use guizero's Animation class to create dice rolling animations for a more interactive experience.

- 
Create a game interface: Design a user interface that includes a score tracker, player names, and buttons for different game actions.

These are just a few suggestions to enhance the dice rolling game. Feel free to explore and implement additional features based on your preferences.

## Project Four: Create a username generator <a name="interactive"></a>
It's time to get into the really interactive part and make a GUI application that generate a random username. Faker is a widely-used library for generating fake data, including names. It provides a range of methods to generate names in various languages and formats. You can install it using pip with the command.
open the terminal and run. `pip install Faker`

```python
from guizero import App, Text, PushButton
from faker import Faker

fake = Faker()

# Function to generate a random name
def gen_name():
    name = fake.name()
    names.value = name

# Create the app window
app = App("Username Generator", bg='orange')

# Create the widgets
message = Text(app, text="Click here to generate the username")
button = PushButton(app, gen_name, text="Generate")
button.text_color = '#ffffff'
button.bg = 'red'
names = Text(app, text='', color='#ffffff', size=34)

# Display the app window
app.display()


```
The code creates a GUI window using the guizero library. When the "Generate" button is clicked, it calls the gen_name function, which generates a random name using the fake.name() method from the faker library and displays it in a larger text size below the button.

Running this code will display an app window titled "Username Generator" with a button labeled "Generate." When you click the button, it will generate a random name and display it in a larger text size below the button.

**Exercise:** Create a pass_key generator, check example <a href="https://drive.google.com/file/d/1yUI6QDVqBErs5mIdo9EPrjAM7qR_yas7/view?usp=share_link">here</a>

## Project Five: Create a meme Generator <a name="meme"></a>
It's time to get into the really interactive part and Start by creating a simple GUI with two text boxes for the top and bottom text. This is where you will enter the text which will be inserted over your picture to create your meme. Add this line to import the widgets needed.

```python
from guizero import App, Drawing, Slider, Combo, TextBox

# App
app = App("Meme Generator", bg="lightgray")

# Function to draw the meme
def draw_meme():
    meme.clear()
    meme.image(0, 0, "cat-133_128.gif")
    meme.text(
        0, 0, top.value,
        color=color.value,
        size=size.value,
        font=font.value,
    )
    meme.text(
        0, 200, bottom.value,
        color=color.value,
        size=size.value,
        font=font.value,
    )

# TextBox
top = TextBox(app, "top_text", command=draw_meme)
bottom = TextBox(app, "bottom_text", command=draw_meme)

# Drawing
meme = Drawing(app, width="fill", height="fill")

# Combo
color = Combo(app, options=["orange", "red", "blue", "green", "grey"], command=draw_meme, selected="blue")
font = Combo(app, options=["monospace", "verdana", "helvetica", "cursive", "sans-serif"], command=draw_meme)

# Slider
size = Slider(app, start=10, end=100, command=draw_meme)

# Call the draw_meme function
draw_meme()

# Display the app
app.display()

```
The code allows users to enter top and bottom text, select a color and font, and adjust the text size using a slider. The draw_meme function clears the drawing, adds an image at the top left corner, and overlays the entered text based on the user's input.

The code uses the "cat-133_128.gif" image for the meme background. If you have that image file in the same directory as your Python script, the app should display it correctly. Make sure the image file name and path are correct.
Click <a href="https://drive.google.com/file/d/1Os_cQTeH6MB-BOSKcP3OLeteRYsfTBCN/view?usp=share_link">here</a> to access the files

## Project Six: Pop-ups
In this project you're going to learn several functions to demonstrate different types of pop-ups:

- 
show_info function displays an information pop-up using the info function.

- 
show_warning function displays a warning pop-up using the warn function.

- 
show_error function displays an error pop-up using the error function.

- 
ask_question function displays a yes/no question pop-up using the yesno function. It shows a response based on the user's selection.


```python
from guizero import App, PushButton, info, warn, error, yesno, question

# App
app = App("GUI Examples")

# Function for info pop-up
def show_info():
    info("Information", "This is an information pop-up!")

# Function for warning pop-up
def show_warning():
    warn("Warning", "This is a warning pop-up!")

# Function for error pop-up
def show_error():
    error("Error", "This is an error pop-up!")

# Function for yes/no question pop-up
def ask_question():
    response = yesno("Question", "Do you like guizero?")
    if response:
        info("Response", "You clicked 'Yes'!")
    else:
        info("Response", "You clicked 'No'!")

# Button for info pop-up
info_button = PushButton(app, text="Info", command=show_info)

# Button for warning pop-up
warning_button = PushButton(app, text="Warning", command=show_warning)

# Button for error pop-up
error_button = PushButton(app, text="Error", command=show_error)

# Button for yes/no question pop-up
question_button = PushButton(app, text="Question", command=ask_question)

# Display the app
app.display()
```
## Project Seven: Calculator App <a name="calc"></a>
In this code, a 2D list named button_layout is used to define the layout of the calculator buttons. Each inner list represents a row of buttons, and each element represents a button label. The layout is used to create the button grid dynamically.

```python
from guizero import App, Box, PushButton, Text

# Function to update the display
def update_display(text):
    display.value += text

# Function to calculate the result
def calculate_result():
    try:
        result = eval(display.value)
        display.value = str(result)
    except:
        display.value = "Error"

# Function to clear the display
def clear_display():
    display.value = ""

# Create the app
app = App("Calculator", width=600, height=800)

# Create the display box
display_box = Box(app, width="fill", height=100, align="top")
display = Text(display_box, text="", size=40)

# Define the button layout
button_layout = [
    ["7", "8", "9", "/"],
    ["4", "5", "6", "*"],
    ["1", "2", "3", "-"],
    ["0", ".", "=", "+"],
    ["C"]
]

# Create the button grid
button_box = Box(app, width="fill", height="fill", layout="grid")

# Create the buttons
buttons = []
for row, row_buttons in enumerate(button_layout):
    for col, label in enumerate(row_buttons):
        button = PushButton(
            button_box, text=label, grid=[col, row],
            width=7, height=5, padx=10, pady=10
        )
        button.bg = "white"
        button.text_color = "black"
        
        if label == "C":
            button.update_command(clear_display)
        elif label == "=":
            button.update_command(calculate_result)
        else:
            button.update_command(update_display, [label])
        
        buttons.append(button)

# Display the app
app.display()

```
The functions update_display, calculate_result, and clear_display handle the button actions.

Inside the nested loop that iterates over the button_layout, the buttons are created dynamically using the label from the layout. The commands for the buttons are set based on the label, and the buttons are added to the buttons list.

## Project Eight: Tic Tac Toe Game <a name="ttt"></a>
Create a simple Tic Tac Toe game using guizero that defines functions to handle various game actions such as clearing the board, choosing a square, taking turns, checking for a win, counting moves, resetting the game, and disabling buttons.

```python
#imports
from guizero import App, Box, PushButton, Text

# Functions
def clear_board():
    new_board = [[None, None, None], 
                 [None, None, None], 
                 [None, None, None]]
    # generate a 3x3 grid
    for x in range(3):
        for y in range(3):
            button = PushButton(
                board, text='', grid=[x, y], width=3, command=choose_square, args=[x,y])
            new_board[x][y] = button
    return new_board

def choose_square(x, y):
    board_square[x][y].text = turn
    board_square[x][y].disable()
    take_turns()
    check_win()
    
def take_turns():
    global turn
    if turn == "X":
        turn = "O"
    else:
        turn = "X"
    message.value = "It's your turn, " + turn
    
def check_win():
    winner = None
    
    # vertical lines
    if(
        board_square[0][0].text == board_square[0][1].text == board_square[0][2].text
    ) and board_square[0][2].text in ["X", "O"]:
        winner = board_square[0][0]
    elif (
        board_square[1][0].text == board_square[1][1].text == board_square[1][2].text
    ) and board_square[1][2].text in ["X", "O"]:
        winner = board_square[1][0]
    elif (
        board_square[2][0].text == board_square[2][1].text == board_square[2][2].text
    ) and board_square[2][2].text in ["X", "O"]:
        winner = board_square[2][0]
        
    # horizontal
    elif (
        board_square[0][0].text == board_square[1][0].text == board_square[2][0].text
    ) and board_square[2][0].text in ["X", "O"]:
        winner = board_square[0][0]
    elif (
        board_square[0][1].text == board_square[1][1].text == board_square[2][1].text
    ) and board_square[2][1].text in ["X", "O"]:
        winner = board_square[0][1]   
    elif (
        board_square[0][2].text == board_square[1][2].text == board_square[2][2].text
    ) and board_square[2][2].text in ["X", "O"]:
        winner = board_square[0][2]  
        
    # diagonals
    elif (
        board_square[0][0].text == board_square[1][1].text == board_square[2][2].text
    ) and board_square[2][2].text in ["X", "O"]:
        winner = board_square[0][0]   
    elif (
        board_square[2][0].text == board_square[1][1].text == board_square[0][2].text
    ) and board_square[0][2].text in ["X", "O"]:
        winner = board_square[0][2]  
    
    if winner is not None:
        message.value = winner.text + " wins!"
    elif moves_taken() == 9:
        message.value = "It's a tie🤝🤝"
        disable_buttons()
    
def moves_taken():
    moves = 0
    for row in board_square:
        for col in row:
            if col.text == "X" or col.text == "O":
                moves = moves + 1
    return moves 

def reset_game():
    global turn
    turn = "X"
    message.value = "It's your turn, " + turn
    for row in board_square:
        for col in row:
            col.text = ""
            col.enable()

def disable_buttons():
    for row in board_square:
        for col in row:
            col.disable()
               
    
# Variables
turn = "X"

# App
app = App('Tic Tac Toe Game', bg='burlywood')
board = Box(app, layout='grid') # Create the board        
board_square = clear_board()
message = Text(app, text="It is your turn, " + turn)
message.text_color = "green"

# Display app
app.display()
```
The game interface is created using guizero's App and Box components. The board is represented as a 3x3 grid of PushButton objects within the board box. Each button corresponds to a square on the board and has a command assigned to it to handle user input. The game state is tracked using a 2D list board_square, where each element represents a button/square on the board.

The check_win function checks for winning conditions by comparing the text values of the buttons in various winning combinations (vertical, horizontal, and diagonal lines). If a winner is found, the appropriate message is displayed. If no winner is found and all squares are filled, it's considered a tie.

## Project Nine: Emoji Match Game<a name="emoji"></a>


## Summary
Guizero aims to make the process of developing quick GUIs simple, approachable, and accessible for new users. There is no need to install additional libraries as it works with the standard Python Tkinter GUI library.

## References
[1]: https://docs.python.org/3/library/tkinter.html
Guizero Github Page: https://github.com/lawsie/guizero

Python Official Docs, Tkinter: https://docs.python.org/3/library/tkinter.html
