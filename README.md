# codsoft
__________________________________'''TASK - 1 CALCULATOR'''__________________________________Here's a simple example of a Calculator program in Python:


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
