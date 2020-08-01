from tkinter import *
import sqlite3

from PIL import Image,ImageTk

root = Tk()
root.geometry('500x500')
root.title("Registration Form")

Firstname=StringVar()
Lastname=StringVar()
Email=StringVar()
var = IntVar()
s=StringVar()
Country=StringVar()
var1= IntVar()

def database():
   name1=Firstname.get()
   name2=Lastname.get()
   email=Email.get()
   gender=var.get()
   state=s.get()
   country=Country.get()
   prog=var1.get()
   conn = sqlite3.connect('ssforms.db')
   with conn:
      cursor=conn.cursor()
   cursor.execute('CREATE TABLE IF NOT EXISTS Atttendees (Firstname TEXT,Lastname TEXT,Email TEXT,Gender TEXT,State TEXT,country TEXT,Programming TEXT)')
   cursor.execute('INSERT INTO Atttendees (Firstname,Lastname,Email,Gender,State,country,Programming) VALUES(?,?,?,?,?,?,?)',(name1,name2,email,gender,state,country,prog,))
   conn.commit()
    
             
label1= Label(root,text="REGISTRATION FORM",font=("Arial bold",30),width=30,bg="pink",fg="black").grid(row=0,column=1)

label2= Label(root,text="First Name",font=("Arial bold",20),width=20).grid(row=1,column=0)
entry2= Entry(root,textvar=Firstname).grid(row=1, column=1)

label3= Label(root,text="Last Name",font=("Arial bold",20),width=20).grid(row=2,column=0)
entry3= Entry(root,textvar=Lastname).grid(row=2, column=1)

label4= Label(root,text="Email",font=("Arial bold",20),width=20).grid(row=3,column=0)
entry4= Entry(root,textvar=Email).grid(row=3, column=1)

label5= Label(root,text="Gender",font=("Arial bold",20),width=20).grid(row=4,column=0)
var=IntVar()
r1=Radiobutton(root,text="Male",padx=5,variable=var,value=1).grid(row=4 ,column=1)
r2=Radiobutton(root,text="Female",padx=10,variable=var,value=2).grid(row=4 ,column=2)

label6= Label(root,text="State",font=("Arial bold",20),width=20).grid(row=5,column=0)
list6= ["Karnataka", "Kerala", "Andhra Pradesh", "Telangana", "Tamilnadu"];
s=StringVar()
droplist=OptionMenu(root,s,*list6)
droplist.config(width=30)
s.set("Belongs to which State")
droplist.grid(row=5,column=1)

label7= Label(root,text="country",font=("Arial bold",20),width=20).grid(row=6,column=0)
entry4= Entry(root,textvar=Country).grid(row=6, column=1)

label8= Label(root,text="Programming Language",font=("Arial bold",20),width=20).grid(row=7,column=0)
var1=IntVar()
Checkbutton(root,text="Java",variable=var1).grid(row=7,column =1)
var2=IntVar()
Checkbutton(root,text="Python",variable=var2).grid(row=8,column =1)
var3=IntVar()
Checkbutton(root,text="c",variable=var3).grid(row=9,column =1)


B1=Button(root, text="submit",width=20,bg="yellow",fg="black",command=database).grid(row=15, column=1)

#def func():
#    MessageBox.showinfo(title="submission",message="submitted")


C = Canvas(root,width=1000,height=1000)
C.grid(row=17,column=1)
img = PhotoImage(file="C:\\Users\\hp\\Desktop\\picaso.png")
C.create_image(0,0,anchor=NW,image=img)

#grid(row=17,column=1)
    

root.mainloop()
