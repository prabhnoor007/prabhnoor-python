from tkinter import *
win=Tk()
count=0
def add_rec():
    f=open("python2.txt","a")
    PatientID=s1.get()
    doc_name=s2.get()
    dept=s3.get()
    N_beds=s4.get()
    fees=s5.get()
    f.writelines(PatientID.ljust(5)+doc_name.ljust(20)+dept.ljust(20)+N_beds.ljust(20)+fees.ljust(5)+"\n")
    f.close()
def next_rec():
    global count
    i=0
    f=open("python2.txt","r")
    try:
        
        while(i<=count):
            l=f.readline()
            i=i+1

        m=l.split()
        s1.set(m[0])
        s2.set(m[1])
        s3.set(m[2])
        s4.set(m[3])
        s5.set(m[4])
        print(m)
    except:
        clear()
        s6.set("No More Record Found")
    count=count+1
    f.close()
def prev_rec():
    global count
    f=open("python2.txt","r")
    i=0
    if(count<=0):
        messagebox.showinfo("No previous record")
    else:
        while(i<=(count-1)):
            l=f.readline()
            i=i+1
        l1=l.split()
        s1.set(l1[0])
        s2.set(l1[1])
        s3.set(l1[2])
        s4.set(l1[3])
        s5.set(l1[4])
        count=count-1
    f.close()
def delrec():
    k=[s1.get(),s2.get(),s3.get(),s4.get(),s5.get()]
    f=open("python2.txt","r")
    lines=f.readlines()
    print(lines)
    print(k)
    f.close()
    f=open("python2.txt","w")
    for i in lines:
        m=i.split()
        print(m)
        if(m!=k):
             f.writelines(m[0].ljust(3)+m[1].ljust(20)+m[2].ljust(20)+m[3].ljust(20)+m[4].ljust(5)+"\n")
    f.close()
def search():
    k=s1.get()
  
    f=open("python2.txt","r")
    h=f.readlines()
    for i in h:
        j=i.split()
        if(j[0]==k):
            print("patient found") 
            print(j)
            s1.set(j[0])
            s2.set(j[1])
            s3.set(j[2])
            s4.set(j[3])
            s5.set(j[4])
            
    f.close()
def first_rec():
    f=open("python2.txt","r")
    l=f.readline()
    try:
        l1=l.split()
        s1.set(l1[0])
        s2.set(l1[1])
        s3.set(l1[2])
        s4.set(l1[3])
        s5.set(l1[4])
    except IndexError:
        messagebox.showinfo("No Record")
    f.close()

def last_rec():
     f=open("python2.txt","r")
     l=f.readlines()
     try:
         l=l[len(l)-1]
         l1=l.split()
         s1.set(l1[0])
         s2.set(l1[1])
         s3.set(l1[2])
         s4.set(l1[3])
         s5.set(l1[4])
     except:
        messagebox.showinfo("No Record")
     f.close()


def update():
    a1=s1.get()
    a2=s2.get()
    a3=s3.get()
    a4=s4.get()
    a5=s5.get()
    f=open("python2.txt","r")
    h=f.readlines()
    f.close()
    f=open("python2.txt","w")
    for i in h:
        j=i.split()
        if(j[0]!=a1):
            f.writelines(j[0].ljust(3)+j[1].ljust(20)+j[2].ljust(20)+j[3].ljust(20)+j[4].ljust(5)+"\n")
    
        else:
            f.writelines(j[0].ljust(3)+a2.ljust(20)+a3.ljust(20)+a4.ljust(20)+a5.ljust(5)+"\n")
    
    
    
    
def clear():
    m=""
    s1.set(m)
    s2.set(m)
    s3.set(m)
    s4.set(m)
    s5.set(m)
s1=StringVar()
s2=StringVar()
s3=StringVar()
s4=StringVar()
s5=StringVar()
s6=StringVar()
l1=Label(win,text="Patient_ID")
l2=Label(win,text="Doctor_name")
l3=Label(win,text="Department")
l4=Label(win,text="No_of_Beds")
l5=Label(win,text="Fees")
t1=Entry(win,textvariable=s1)
t2=Entry(win,textvariable=s2)
t3=Entry(win,textvariable=s3)
t4=Entry(win,textvariable=s4)
t5=Entry(win,textvariable=s5)
t6=Entry(win,textvariable=s6)
b1=Button(win,text="add",command=add_rec)
b2=Button(win,text=">",command=next_rec)
b3=Button(win,text="delete",command=delrec)
b4=Button(win,text="search",command=search)
b5=Button(win,text="update",command=update)
b6=Button(win,text="clear",command=clear)
b7=Button(win,text="<",command=prev_rec)
b8=Button(win,text="First",command=first_rec)
b9=Button(win,text="Last",command=last_rec)
l1.grid(row=1,column=1)
l2.grid(row=2,column=1)
l3.grid(row=1,column=3)
l4.grid(row=2,column=3)
l5.grid(row=3,column=1)
t1.grid(row=1,column=2)
t2.grid(row=2,column=2)
t3.grid(row=1,column=4)
t4.grid(row=2,column=4)
t5.grid(row=3,column=2)
t6.grid(row=3,column=7)
b1.grid(row=5,column=1)
b2.grid(row=5,column=2)
b3.grid(row=5,column=3)
b4.grid(row=5,column=4)
b5.grid(row=5,column=5)
b6.grid(row=6,column=1)
b7.grid(row=6,column=2)
b8.grid(row=6,column=3)
b9.grid(row=6,column=4)
win.mainloop()

