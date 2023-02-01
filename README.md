import socket

#Create a function to check the server status
def checkServer(ip):
   try:
      #Create a socket and connect to the given IP
      s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
      s.connect((ip, 80))
      print("Server is Up")
   except socket.error as e:
      print("Server is Down")

#Create a GUI using tkinter
from tkinter import *
root = Tk()

#Create a label widget to hold a description
desc = Label(root, text="Enter IP Address: ")
desc.grid(row=0, column=0)

#Create an Entry widget to accept ip address
ip_entry = Entry(root)
ip_entry.grid(row=0, column=1)

#Create a button to call the function
check_btn = Button(root, text="Check Server", command=lambda: checkServer(ip_entry.get()))
check_btn.grid(row=1, column=1)

root.mainloop()
