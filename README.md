# codsoft
__________________________________'''TASK - 1 CALCULATOR'''__________________________________
class Calculator:
    def add(self, num1, num2):
        return num1 + num2

    def subtract(self, num1, num2):
        return num1 - num2

    def multiply(self, num1, num2):
        return num1 * num2

    def divide(self, num1, num2):
        if num2 == 0:
            raise ZeroDivisionError("Cannot divide by zero")
        return num1 / num2

def main():
    calculator = Calculator()

    while True:
        print("\nCalculator Menu:")
        print("1. Addition")
        print("2. Subtraction")
        print("3. Multiplication")
        print("4. Division")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice in ["1", "2", "3", "4"]:
            try:
                num1 = float(input("Enter first number: "))
                num2 = float(input("Enter second number: "))

                if choice == "1":
                    result = calculator.add(num1, num2)
                    print(f"{num1} + {num2} = {result}")
                elif choice == "2":
                    result = calculator.subtract(num1, num2)
                    print(f"{num1} - {num2} = {result}")
                elif choice == "3":
                    result = calculator.multiply(num1, num2)
                    print(f"{num1} * {num2} = {result}")
                elif choice == "4":
                    try:
                        result = calculator.divide(num1, num2)
                        print(f"{num1} / {num2} = {result}")
                    except ZeroDivisionError as e:
                        print(str(e))
            except ValueError:
                print("Invalid input. Please enter a number.")
        elif choice == "5":
            break
        else:
            print("Invalid choice. Please choose a valid option.")

if __name__ == "__main__":
    main()

****************************************************************************************************************************************************************************
____________________________________TASK - 2 TO DO-LIST____________________________________

tasks = []

def add_task():
    task = input("Enter a task: ")
    tasks.append({"task": task, "done": False})
    print(f"Task '{task}' added.")

def view_tasks():
    if not tasks:
        print("No tasks available.")
    else:
        for index, task in enumerate(tasks, start=1):
            status = "Done" if task["done"] else "Not Done"
            print(f"{index}. {task['task']} - {status}")

def delete_task():
    if not tasks:
        print("No tasks available.")
    else:
        view_tasks()
        try:
            task_number = int(input("Enter task number to delete: "))
            task = tasks.pop(task_number - 1)
            print(f"Task '{task['task']}' deleted.")
        except (ValueError, IndexError):
            print("Invalid task number.")

def mark_as_done():
    if not tasks:
        print("No tasks available.")
    else:
        view_tasks()
        try:
            task_number = int(input("Enter task number to mark as done: "))
            tasks[task_number - 1]["done"] = True
            print(f"Task '{tasks[task_number - 1]['task']}' marked as done.")
        except (ValueError, IndexError):
            print("Invalid task number.")

def mark_as_not_done():
    if not tasks:
        print("No tasks available.")
    else:
        view_tasks()
        try:
            task_number = int(input("Enter task number to mark as not done: "))
            tasks[task_number - 1]["done"] = False
            print(f"Task '{tasks[task_number - 1]['task']}' marked as not done.")
        except (ValueError, IndexError):
            print("Invalid task number.")

while True:
    print("\nTo-Do List Menu:")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Delete Task")
    print("4. Mark Task as Done")
    print("5. Mark Task as Not Done")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_task()
    elif choice == "2":
        view_tasks()
    elif choice == "3":
        delete_task()
    elif choice == "4":
        mark_as_done()
    elif choice == "5":
        mark_as_not_done()
    elif choice == "6":
        break
    else:
        print("Invalid choice. Please choose a valid option.")



        ****************************************************************************************************************************************************************************
____________________________________________________TASK-3  PASSWORD GENERATOR____________________________________________________
import random
import string

def password_generator(length):
    all_characters = string.ascii_letters + string.digits + string.punctuation
    if length < 8:
        print("Password length should be at least 8 characters.")
        return None
    password = ''.join(random.choice(all_characters) for i in range(length))
    return password

def custom_password_generator(length, use_uppercase, use_numbers, use_special_chars):
    characters = string.ascii_lowercase
    if use_uppercase:
        characters += string.ascii_uppercase
    if use_numbers:
        characters += string.digits
    if use_special_chars:
        characters += string.punctuation
    if length < 8:
        print("Password length should be at least 8 characters.")
        return None
    password = ''.join(random.choice(characters) for i in range(length))
    return password

def main():
    print("Password Generator Menu:")
    print("1. Generate a random password")
    print("2. Customize your password")
    choice = input("Enter your choice: ")

    if choice == "1":
        length = int(input("Enter the length of the password: "))
        password = password_generator(length)
        if password:
            print(f"Generated Password: {password}")
    elif choice == "2":
        length = int(input("Enter the length of the password: "))
        use_uppercase = input("Include uppercase letters? (yes/no): ").lower() == "yes"
        use_numbers = input("Include numbers? (yes/no): ").lower() == "yes"
        use_special_chars = input("Include special characters? (yes/no): ").lower() == "yes"
        password = custom_password_generator(length, use_uppercase, use_numbers, use_special_chars)
        if password:
            print(f"Generated Password: {password}")
    else:
        print("Invalid choice.")

if _name_ == "_main_":
    main()
