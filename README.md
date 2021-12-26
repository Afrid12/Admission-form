# Admission-form
#project using python
..................................................................................................................................................
from tkinter import *
from tkinter import messagebox
from tkinter.ttk import *
import datetime
import mysql.connector


def insertdata():

    enq_course=b1.get()
    candidates_name=c1.get()
    fathers_name=d1.get()
    contact_number=e1.get()
    aadhar_number=f1.get()
    permanent_address=g1.get()
    DOB=h1.get()
    nationality=i1.get()
    sex=j1.get()
    religion=k1.get()
    general_category=l1.get()
    education_qualification=m1.get()
    languages_known=n1.get()
    email_id=e3.get()
    candidates_profile=o1.get()
    date=datetime.date.today()
    date1=(str(date))

    con=mysql.connector.connect(user='root',password='admin',host='localhost',database='afrid')
    cur=con.cursor()
    query=("insert into admission_form  (enq_course,candidates_name,fathers_name,contact_number,aadhar_number,permanent_address,DOB,nationality,sex,religion,general_category,education_qualification,languages_known,email_id,candidates_profile,enq_date) values ('"+enq_course+"','"+candidates_name+"','"+fathers_name+"','"+contact_number+"','"+aadhar_number+"','"+permanent_address+"','"+DOB+"','"+nationality+"','"+sex+"','"+religion+"','"+general_category+"','"+education_qualification+"','"+languages_known+"','"+email_id+"','"+candidates_profile+"','"+date1+"');")
    
    cur.execute(query)
    cur.execute("select * from admission_form")
    
    for row in cur.fetchall():
        print("",row[0],"",row[1],"",row[2],"",row[3],"",row[4],"",row[5],"",row[6],"",row[7],"",row[8])
    con.commit()
    con.close()
    messagebox.showinfo("status","Record Inserted")
    
    
    b1.delete(0,len(enq_course))
    c1.delete(0,len(candidates_name))
    d1.delete(0,len(fathers_name))
    e1.delete(0,len(contact_number))
    f1.delete(0,len(aadhar_number))
    g1.delete(0,len(permanent_address))
    h1.delete(0,len(DOB))
    i1.delete(0,len(nationality))
    j1.delete(0,len(sex))
    k1.delete(0,len(religion))
    l1.delete(0,len(general_category))
    m1.delete(0,len(education_qualification))
    n1.delete(0,len(languages_known))
    e3.delete(0,len(email_id))
    o1.delete(0,len(candidates_profile))
       
    

#TITLE & window config
var=Tk()
var.title("ADMISSION FORM")
var.minsize(500,500)




#ENQUIRY OF COURSE LABEL & ENTRY

b=Label(var , text="ENTER THE COURSE NAME")
b1=Entry(var)
b.grid(row=0,column=2)
b1.grid(row=0,column=3)

#ENTRY OF STUDENT NAME LABEL & ENTRY
c=Label(var,text="ENTER CANDIDATE'S NAME")
c1=Entry(var)
c.grid(row=1,column=0)
c1.grid(row=1,column=1)

#ENTRY OF FATHER'S NAME LABEL & ENTRY
d=Label(var,text="ENTER FATHER'S NAME")
d1=Entry(var)
d.grid(row=1,column=3)
d1.grid(row=1,column=4)

#ENTRY OF CANDIDATES CONTACT NUMBER
e=Label(var,text="CONTACT NUMBER")
e1=Entry(var)
e.grid(row=2,column=0)
e1.grid(row=2,column=1)


#ENTRY OF AADHAR CARD NUMBER
f=Label(var, text="AADHAR NUMBER")
f1=Entry(var)
f.grid(row=2,column=2)
f1.grid(row=2,column=3)


#ENTRY OF PERMANENT ADDRESS

g=Label(var,text="PERMANENT ADDRESS")
g1=Entry(var)
g.grid(row=3,column=0)
g1.grid(row=3,column=1)

#ENTRY OF DATE OF BIRTH

h=Label(var,text="DOB")
h1=Entry(var)
h.grid(row=3,column=3)
h1.grid(row=3,column=4)

#ENTRY OF STUDENT'S NATIONALITY

i=Label(var,text="NATIONALITY")
i1=Entry(var)
i.grid(row=4,column=0)
i1.grid(row=4,column=1)



#ENTRY OF STUDENT'S GENDER
j=Label(var,text="SEX")
j.grid(row=4,column=2)
j1=Entry(var)
j1.grid(row=4,column=3)

# HERE WRITE ABOUT YOUR GENDER
#"MALE"
#"FEMALE"
#"OTHERS"

#ENTRY OF RELIGION

k=Label(var,text="RELIGION")
k1=Entry(var)
k.grid(row=5,column=0)
k1.grid(row=5,column=1)

# HER WRITE YOUR RELIGION
# HINDU
# MUSLIM
# CHRISTIAN
# SIKH
# AND ALL etc

#ENTRY OF RELIGION CATEGORY.

l=Label(var,text="GENERAL CATEGORY")
l1=Entry(var)
l.grid(row=5,column=3)
l1.grid(row=5,column=4)

#ENTRY OF EDUCATION QUALIFICATION

m=Label(var,text="EDUCATION QUALIFICATION")
m.grid(row=6,column=0)
m1=Entry(var)
m1.grid(row=6,column=1)

#ENTRY OF LANGUAGES KNOWN

n=Label(var,text="LANGUAGES KNOWN")
n1=Entry(var)
n.grid(row=6,column=2)
n1.grid(row=6,column=3)


#ENTRY OF E-MAIL ID
e2=Label(var,text="E-Mail ID")
e2.grid(row=7,column=0)
e3=Entry(var)
e3.grid(row=7,column=1)


#ENTRY OF CANDIDATES PROFILE

o=Label(var,text="CANDIDATES PROFILE")
o1=Entry(var)
o.grid(row=7,column=3)
o1.grid(row=7,column=4)


#("HERE WRITE ABOUT YOUR WORK")
# "STUDENT"
# "GOVT.,EMPLOY"
# "Pvt.SECTOR EMPLOY"
# "BUSINESSMAN"
# "DEFENSE PROFESSIONEL"
# "Retd., PERSON"
# "HOUSE WIFE"
# "OTHERS"


#BUTTON to submit
submit=Button(var,text="SUBMIT",command=insertdata)
submit.grid(row=9,column=2)

var.mainloop()
