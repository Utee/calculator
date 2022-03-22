# Mapisaunga Takudzwa Blessing M00836627
# Utibe-Abasi Jacob Udoh M00790353

import threading
import tkinter.messagebox
from tkinter import *
import math

# ----------------FUNCTIONS FOR THE BUTTONS-----------------------#
# This function updates the input field when a number is entered.
def Click(number):
    global num
    num += str(number)
    input_num.set(num)

# This function is used to clear the whole input field.
def Clear():
    # Clear output text
    global num
    num = ''
    input_num.set(0)

# Function with the error message.
def message():
    Clear()
    tkinter.messagebox.showinfo('ERROR', 'You can not divide a number by zero.')

# This function is used to display the result of the entry in the input field.
def Equal():
    global num
    try:
        # eval:This function is used to evaluates the string expression directly
        result = eval(num)
        input_num.set(result)
    except ZeroDivisionError:
        thread = threading.Thread(target=message())
        thread.start()

# Function to find the square root of a number.
def Squareroot():
    global num
    try:
        sqrt = math.sqrt(float(num))
        input_num.set(sqrt)
    except ValueError:
        thread = threading.Thread(target=message())
        thread.start()

# Function too find the cube root of a number.
def Cuberoot():
    global num
    if int(num) < 0:
        num = abs(int(num))
        cube = float(num) ** (1 / 3) * (-1)
    else:
        cube = float(num) ** (1 / 3)
    input_num.set(cube)

# Function to negate a number.
def negate():
    global num
    current = '-' + num
    num = current
    input_num.set(current)

# Function to give the value of a number to the power of two.
def Power():
    global num
    try:
        power = str(math.pow(int(num), 2))
        input_num.set(power)
    except ValueError:
        thread = threading.Thread(target=message())
        thread.start()

# Function to calculate the pi value of a number.
def pi():
    global num
    try:
        current = math.pi
        pie = float(num) * current
        input_num.set(pie)
    except ValueError:
        thread = threading.Thread(target=message())
        thread.start()

# Function to clear the input field one number at a time.
def backspace():
    global num
    num = num[:-1]
    input_num.set(num)
    numlen = len(num)
    if numlen == 0:
        input_num.set(0)

# Function to calculate the percentage of a number.
def Percent():
    global num
    current = str(eval(num + '/100'))
    num = current
    input_num.set(current)


window = Tk()  # Creating a basic window.
window.configure(background='Gray12')  # Configuring the color of the window.
window.geometry('320x400')  # This is for setting the size of the window.
window.resizable(0, 0)  # This is to make sure that the window does not resize.
window.title('Course Work 3.')  # This is the title of the window.
calctitle = Label(window, text='Calculator.', pady=10, bg='Gray12', fg='White',
                  font=('Brush Script MT', 22, 'bold'))
calctitle.grid(row=0, column=0, columnspan=1)

num = ''
input_num = StringVar(window)
input_num.set('0')
# ******************** INPUT FRAME **************************
input_frame = Frame(window, bd=0, padx=3, pady=5, bg='Gray12')
input_frame.grid(row=1, column=0)
# This is where the values and expressions are going to be input on the calculator.
input_value = Entry(input_frame, font=('Lucida Sans', 15, 'bold'), fg='White',
                    textvariable=input_num, width=24, bg='Gray12', bd=0, justify=RIGHT)
input_value.grid(row=0, column=1)

# ******************** BUTTONS FRAME ************************
buttons = Frame(window, bg='Gray12')
buttons.grid(row=2, column=0)

# First row.
percentbtn = Button(buttons, text='%', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                    bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=Percent()))
percentbtn.grid(row=0, column=0, padx=1, pady=1)

clear = Button(buttons, text='C', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=Clear()))
clear.grid(row=0, column=1, padx=1, pady=1)

backspace = Button(buttons, text='←', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                   bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=backspace))
backspace.grid(row=0, column=2, padx=1, pady=1)

multiply = Button(buttons, text='×', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                  bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('*'))
multiply.grid(row=0, column=3, padx=1, pady=1)

devide = Button(buttons, text='÷', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('/'))
devide.grid(row=0, column=4, padx=1, pady=1)

# Second row.
seven = Button(buttons, text='7', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Black', cursor='hand2', command=lambda: Click(7))
seven.grid(row=1, column=0, padx=1, pady=1)

eight = Button(buttons, text='8', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Black', cursor='hand2', command=lambda: Click(8))
eight.grid(row=1, column=1, padx=1, pady=1)

nine = Button(buttons, text='9', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Black', cursor='hand2', command=lambda: Click(9))
nine.grid(row=1, column=2, padx=1, pady=1)

plus = Button(buttons, text='+', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Gray4', cursor='hand2', command=lambda: Click("+"))
plus.grid(row=1, column=3, padx=1, pady=1)

minus = Button(buttons, text=' ̶', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('-'))
minus.grid(row=1, column=4, padx=1, pady=1)

# Third row.
four = Button(buttons, text='4', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Black', cursor='hand2', command=lambda: Click(4))
four.grid(row=2, column=0, padx=1, pady=1)

five = Button(buttons, text='5', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Black', cursor='hand2', command=lambda: Click(5))
five.grid(row=2, column=1, padx=1, pady=1)

six = Button(buttons, text='6', fg='White', width=8, height=3, font=('Lucida Sans', 8),
             bd=0, bg='Black', cursor='hand2', command=lambda: Click(6))
six.grid(row=2, column=2, padx=1, pady=1)

bracket1 = Button(buttons, text="(", fg='White', width=8, height=3, font=('Lucida Sans', 8),
                  bd=0, bg='Gray4', cursor='hand2', command=lambda: Click("("))
bracket1.grid(row=2, column=3, padx=1, pady=1)

bracket2 = Button(buttons, text=")", fg='White', width=8, height=3, font=('Lucida Sans', 8),
                  bd=0, bg='Gray4', cursor='hand2', command=lambda: Click(")"))
bracket2.grid(row=2, column=4, padx=1, pady=1)

# Fourth row.
one = Button(buttons, text='1', fg='White', width=8, height=3, font=('Lucida Sans', 8),
             bd=0, bg='Black', cursor='hand2', command=lambda: Click(1))
one.grid(row=3, column=0, padx=1, pady=1)

two = Button(buttons, text='2', fg='White', width=8, height=3, font=('Lucida Sans', 8),
             bd=0, bg='Black', cursor='hand2', command=lambda: Click(2))
two.grid(row=3, column=1, padx=1, pady=1)

three = Button(buttons, text='3', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Black', cursor='hand2', command=lambda: Click(3))
three.grid(row=3, column=2, padx=1, pady=1)

square_root = Button(buttons, text='√', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                     bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=Squareroot()))
square_root.grid(row=3, column=3, padx=1, pady=1)

cube_root = Button(buttons, text='\u00B3√', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                   bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=Cuberoot()))
cube_root.grid(row=3, column=4, padx=1, pady=1)

# Fifth row.
POW = Button(buttons, text='x\u00B2', fg='White', width=8, height=3, font=('Lucida Sans', 8),
             bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=Power()))
POW.grid(row=4, column=0, padx=1, pady=1)

POW3 = Button(buttons, text='x\u00B3', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('**3'))
POW3.grid(row=4, column=1, padx=1, pady=1)

POWn = Button(buttons, text='x^n', fg='White', width=8, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('**'))
POWn.grid(row=4, column=2, padx=1, pady=1)

plusorminus = Button(buttons, text='±', fg='White', width=8, height=3, font=('Lucida Sans', 8),
                     bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=negate()))
plusorminus.grid(row=4, column=3, padx=1, pady=1)

PI = Button(buttons, text='∏', fg='White', width=8, height=3, font=('Lucida Sans', 8),
            bd=0, bg='Gray4', cursor='hand2', command=lambda: threading.Thread(target=pi()))
PI.grid(row=4, column=4, padx=1, pady=1)

# Sixth row.
zero = Button(buttons, text='0', fg='White', width=17, height=3, font=('Lucida Sans', 8),
              bd=0, bg='Gray4', cursor='hand2', command=lambda: Click(0))
zero.grid(row=5, column=0, columnspan=2, padx=1, pady=1)

point = Button(buttons, text='.', fg='White', width=8, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Gray4', cursor='hand2', command=lambda: Click('.'))
point.grid(row=5, column=2, padx=1, pady=1)

equal = Button(buttons, text='=', fg='White', width=17, height=3, font=('Lucida Sans', 8),
               bd=0, bg='Midnight Blue', cursor='hand2', command=lambda: threading.Thread(target=Equal()))
equal.grid(row=5, column=3, columnspan=2, padx=1, pady=1)

window.mainloop()
