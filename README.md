import random
import pyperclip
from tkinter import *
from tkinter.ttk import *

# Function for calculation of password
def low():
entry.delete(0, END)

# Get the length of password
length = var1.get()

lower = &quot;abcdefghijklmnopqrstuvwxyz&quot;
upper = &quot;ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz&quot;
digits = &quot;ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789
!@#$%^&amp;*()&quot;
password = &quot;&quot;

# if strength selected is low
if var.get() == 1:
for i in range(0, length):
password = password + random.choice(lower)
return password
# if strength selected is medium
elif var.get() == 0:
for i in range(0, length):
password = password + random.choice(upper)
return password

# if strength selected is strong
elif var.get() == 3:
for i in range(0, length):
password = password + random.choice(digits)
return password
else:
print(&quot;Please choose an option&quot;)

# Function for generation of password
def generate():
password1 = low()
entry.insert(10, password1)

# Function for copying password to clipboard
def copy1():
random_password = entry.get()

pyperclip.copy(random_password)

# Main Function

# create GUI window
root = Tk()
var = IntVar()
var1 = IntVar()

# Title of your GUI window
root.title(&quot;Random Password Generator&quot;)

# create label and entry to show
# password generated
Random_password = Label(root, text=&quot;Password&quot;)
Random_password.grid(row=0)
entry = Entry(root)
entry.grid(row=0, column=1)

# create label for length of password
c_label = Label(root, text=&quot;Length&quot;)
c_label.grid(row=1)

# create Buttons Copy which will copy
# password to clipboard and Generate
# which will generate the password
copy_button = Button(root, text=&quot;Copy&quot;, command=copy1)
copy_button.grid(row=0, column=2)
generate_button = Button(root, text=&quot;Generate&quot;, command=generate)
generate_button.grid(row=0, column=3)

# Radio Buttons for deciding the
# strength of password
# Default strength is Medium
radio_low = Radiobutton(root, text=&quot;Low&quot;, variable=var, value=1)
radio_low.grid(row=1, column=2, sticky=&#39;E&#39;)
radio_middle = Radiobutton(root, text=&quot;Medium&quot;, variable=var, value=0)
radio_middle.grid(row=1, column=3, sticky=&#39;E&#39;)
radio_strong = Radiobutton(root, text=&quot;Strong&quot;, variable=var, value=3)
radio_strong.grid(row=1, column=4, sticky=&#39;E&#39;)
combo = Combobox(root, textvariable=var1)

# Combo Box for length of your password
combo[&#39;values&#39;] = (8, 9, 10, 11, 12, 13, 14, 15, 16,

17, 18, 19, 20, 21, 22, 23, 24, 25,
26, 27, 28, 29, 30, 31, 32, &quot;Length&quot;)

combo.current(0)
combo.bind(&#39;&lt;&lt;ComboboxSelected&gt;&gt;&#39;)
combo.grid(column=1, row=1)

# start the GUI
root.mainloop()
