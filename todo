#!/Users/adarshkumar/opt/anaconda3/bin/python

from os import remove
from sys import argv
from datetime import date

my_task = []
my_task_dic = {}


def report():
    # Show the status of the Tasks
    file = open('report.txt', 'r')
    today = date.today()
    d1 = today.strftime("%d/%m/%Y")
    if len(file.readline()) == 0:
        print(f"{d1} Pending : 0 Completed : 0")
        return
    elif len(file.readline()) != 0:
        file.seek(0, 0)
        complete = file.readline()
        pending = file.readline()
        print(f"\x1b[33m{d1} Pending : {int(pending)} Completed : {int(complete)}\x1b[0m", sep='')
        return


def help_module():
    # Reveal all the tasks
    print("\x1b[36m $ python todo.py add 'todo item' \t # Add a new todo \x1b[0m")
    print("\x1b[36m $ python todo.py ls  \t\t\t # Show remmaining todo \x1b[0m")
    print("\x1b[36m $ python todo.py del NUMBER \t\t # Delete a todo  \x1b[0m")
    print("\x1b[36m $ python todo.py done NUMBER  \t\t # Complete a todo \x1b[0m")
    print("\x1b[36m $ python todo.py help \t\t\t # Show Usage\x1b[0m")
    print("\x1b[36m $ python todo.py report \t\t # Statistics \x1b[0m")
    pass


def add_module(msg):
    # Add task to the List
    file = open("todo.txt", 'a')
    report = open('report.txt', 'r')
    temp = open('temp.txt', 'w+')
    test = report.readline()
    if len(test) == 0:
        report = open('report.txt', 'w+')
        report.write("0\n")
        report.write("1\n")
    elif len(test) != 0:
        complete = int(report.readline())
        complete += 1
        report.seek(0,0)
        n = report.readline()
        temp.write(n)
        temp.write(str(complete))
        report.close()
        temp.close()
        report = open('report.txt', 'w+')
        temp = open('temp.txt', 'r')
        report.write(temp.readline())
        report.write(temp.readline())
        report.close()
        temp.close()
        remove('temp.txt')
    file.write(msg + "\n")
    my_task.append(msg)
    print("Added todo: ",msg)
    pass


def ls_module():
    # List the remaining Task
    count = 1
    file = open('todo.txt', 'r+')
    while True:
        msg = file.readline()
        if len(msg) == 0:
            break
        my_task.append(msg)
        count += 1
    count -= 1
    while count != 0:
        print(f"\x1b[35m[{count}] {my_task[count-1]}\x1b[0m", end='')
        count -= 1


def done(index):
    # Remove task from the List
    count = 1
    file = open('todo.txt', 'r+')
    while True:
        msg = file.readline()
        if len(msg) == 0:
            break
        my_task.append(msg)
        count += 1
    my_task.pop(index-1)
    file = open('todo.txt', "w+")
    for i in range(len(my_task)):
        if len(my_task[i]) > 1:
            file.write(my_task[i])
    print(f'Marked todo #{index} as done.')
    report = open('report.txt', 'r')
    temp = open('temp.txt', 'w+')
    test = report.readline()
    if len(test) == 0:
        report = open('report.txt', 'w+')
        report.write("0\n")
        report.write("0\n")
    elif len(test) != 0:
        report.seek(0, 0)
        n = report.readline()
        n = int(n) + 1
        temp.write(str(n) + "\n")
        complete = report.readline()
        complete = int(complete) - 1
        temp.write(str(complete) + "\n")
        report.close()
        temp.close()
        report = open('report.txt', 'w+')
        temp = open('temp.txt', 'r')
        report.write(temp.readline())
        report.write(temp.readline())
        report.close()
        temp.close()
        remove('temp.txt')


def delete_module(index):
    # Delete Task from the List
    count = 1
    file = open('todo.txt', 'r+')
    while True:
        msg = file.readline()
        if len(msg) == 0:
            break
        my_task.append(msg)
        count += 1
    my_task.pop(index - 1)
    file = open('todo.txt', "w+")
    for i in range(len(my_task)):
        if len(my_task[i]) > 1:
            file.write(my_task[i])
    print(f'Deleted todo #{index}')
    report = open('report.txt', 'r')
    temp = open('temp.txt', 'w+')
    test = report.readline()
    if len(test) == 0:
        report = open('report.txt', 'w+')
        report.write("0\n")
        report.write("0\n")
    elif len(test) != 0:
        report.seek(0, 0)
        n = report.readline()
        n = int(n)
        temp.write(str(n) + "\n")
        complete = report.readline()
        complete = int(complete) - 1
        temp.write(str(complete) + "\n")
        report.close()
        temp.close()
        report = open('report.txt', 'w+')
        temp = open('temp.txt', 'r')
        report.write(temp.readline())
        report.write(temp.readline())
        report.close()
        temp.close()
        remove('temp.txt')


# define ANSI_COLOR_RED     "\x1b[31m"
# define ANSI_COLOR_GREEN   "\x1b[32m"
# define ANSI_COLOR_YELLOW  "\x1b[33m"
# define ANSI_COLOR_BLUE    "\x1b[34m"
# define ANSI_COLOR_MAGENTA "\x1b[35m"
# define ANSI_COLOR_CYAN    "\x1b[36m"
# define ANSI_COLOR_RESET   "\x1b[0m"


if len(argv) == 1:
    print("\x1b[36m $ python todo.py add 'todo item' \t # Add a new todo \x1b[0m")
    print("\x1b[36m $ python todo.py ls  \t\t\t # Show remmaining todo \x1b[0m")
    print("\x1b[36m $ python todo.py del NUMBER \t\t # Delete a todo  \x1b[0m")
    print("\x1b[36m $ python todo.py done NUMBER  \t\t # Complete a todo \x1b[0m")
    print("\x1b[36m $ python todo.py help \t\t\t # Show Usage\x1b[0m")
    print("\x1b[36m $ python todo.py report \t\t # Statistics \x1b[0m")

elif len(argv) > 1:
    if argv[1] == "add":
        add_module(argv[2])
    elif argv[1] == "report":
        report()
    elif argv[1] == "help":
        help_module()
    elif argv[1] == "ls":
        ls_module()
    elif argv[1] == "done":
        done(int(argv[2]))
    elif argv[1] == "del":
        delete_module(int(argv[2]))
