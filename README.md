# Create Password Generator
Prompt the user to specify the desired length of the password.
Generate Password: Use a combination of random characters to generate a password of the specified length.
Display the Password: Print the generated password on the screen.
# Create Password Generator
'''
Prompt the user to specify the desired length of the password.
Generate Password: Use a combination of random characters to generate a password of the specified length.
Display the Password: Print the generated password on the screen.'''

import random
import string
from tkinter import *

root = Tk()
root.title("PASSWORD GENERATOR")     # Set the name of the Window's Title
root.config(background = "#95A5A6")  # Set the background of Window
root.geometry("480x300")             # Set the size of the Window

label1 = Label(root, text = "Password Generator", bg ="#95A5A6",  font = ("Arial", 15, "bold", "underline"))  # Main heading of Password Generator
label1.place(x = 30, y = 30)

label2 = Label(root, text = "Enter Password Length: ", bg ="#95A5A6", font = ("Arial", 15, "bold"))   # Ask user to Enter the length of the password 
label2.place(x = 30, y = 90)

e1 = Entry(root, width = 46, font = ("Calibri", 13, "bold"))  # Create the box where user write the length of the password
e1.place(x = 30, y = 133)

label3 = None
label4 = None

def gen():
    global label3, label4
    num = int(e1.get())
    s1 = string.ascii_lowercase
    s2 = string.ascii_uppercase
    s3 = string.digits
    s4 = string.punctuation
    
    s = []         # Create empty list to store all strings 
    s.extend(list(s1))
    s.extend(list(s2))
    s.extend(list(s3))
    s.extend(list(s4))
    
    random.shuffle(s)  # It will shuffle randomly all the string 
    password = ''
    for i in range(num):
        password += random.choice(s)
        if len(password) == num:
            break
        
    if label3:
        label3.destroy()  # Destroy the previous label if it exists
    if label4:
        label4.destroy()  # Destroy the previous label if it exists    
    
    label3 = Label(root, text = "Password: ", bg ="#95A5A6",  font = ("Arial", 15, "bold"))   
    label3.place(x = 30, y = 250)
    
    label4 = Label(root, text = password, bg ="#95A5A6",  font = ("Arial", 15, "bold"))  #Here you get the generated password
    label4.place(x = 150, y = 250)
        
button = Button(root, text = "Generate Password", fg = "Black", bg = "#7dd0b6",  #Create the button of Generate Password
                font = ("times", 15, "bold"), width = 34, command = gen)   
button.place(x = 30, y = 180)

root.mainloop

