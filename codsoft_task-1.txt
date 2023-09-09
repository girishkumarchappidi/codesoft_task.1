from tkinter import *
from tkinter import messagebox

def add():
    task = en.get()
    if task:
        listbox.insert(END, task)
        en.delete(0, END)
    else:
        messagebox.showwarning("Warning", "Enter a task!")

def remove():
    selected_task_index = listbox.curselection()
    if selected_task_index:
        listbox.delete(selected_task_index)
    else:
        messagebox.showwarning("Warning", "Select a task to remove!")

def clear():
    listbox.delete(0,END)

root = Tk()
root.title("To-Do List")

frame = Frame(root)
frame.pack(padx=11, pady=11)

listbox = Listbox(frame, selectmode=SINGLE)
listbox.pack(side=LEFT, fill=BOTH, expand=True)

scrollbar = Scrollbar(frame, orient=VERTICAL)
scrollbar.pack(side=RIGHT, fill=Y)

listbox.config(yscrollcommand=scrollbar.set)
scrollbar.config(command=listbox.yview)

en = Entry(root, width=30)
en.pack(pady=10)

a = Button(root, text="Add Task", command=add,fg='blue')
a.pack(side=LEFT, padx=5)

r = Button(root, text="Remove Task", command=remove,fg='red')
r.pack(side=LEFT, padx=5)

c = Button(root, text="Clear List", command=clear,fg='black')
c.pack(side=LEFT, padx=5)

root.mainloop()