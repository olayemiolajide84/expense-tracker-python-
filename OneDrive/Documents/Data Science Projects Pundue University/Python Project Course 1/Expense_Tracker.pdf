# Personal Expense Tracker

import csv

# Step 1: Add Expense
def add_expense(expenses):
    date = input('Enter date (yyyy-mm-dd): ')
    category = input('Enter expense category (e.g Travel, Entertainment): ')
    amount = float(input('Enter expense amount: '))
    description = input('Enter expense description: ')
    expenses.append({
        'date': date,
        'category': category,
        'amount': amount,
        'description': description
    })
    print('Expense added successfully')


# Step 2: View Expenses
def display_record(expenses):
    if not expenses:
        print('No expense recorded')
    else:
        for expense in expenses:
            if all(key in expense for key in ['date', 'category', 'amount', 'description']):
                print(f"Date: {expense['date']}, Category: {expense['category']}, Amount: {expense['amount']}, Description: {expense['description']}")
            else:
                print(f"Expense record not valid: {expense}")


# Step 3: Set Monthly Budget
def monthly_budget():
    budget = float(input("Enter budget amount: "))
    return budget


# Step 4: Track Budget
def budget_tracking(expenses, budget):
    total_expenses = sum(expense['amount'] for expense in expenses)
    print(f"Total expense: {total_expenses}")
    if total_expenses <= budget:
        print("Expense within budget limit")
    else:
        print(f"Budget limit exceeded by {total_expenses - budget}")


# Step 5: Save to File
def save_file(expenses, filename='expenses.csv'):
    with open(filename, 'w', newline='') as file:
        writer = csv.writer(file)
        writer.writerow(['date', 'amount', 'category', 'description'])
        for expense in expenses:
            writer.writerow([expense['date'], expense['amount'], expense['category'], expense['description']])
    print("File saved successfully")


# Step 6: Load from File
def load_expenses(filename='expenses.csv'):
    expenses = []
    try:
        with open(filename, 'r') as file:
            reader = csv.DictReader(file)
            for row in reader:
                if all(key in row for key in ['date', 'amount', 'category', 'description']):
                    row['amount'] = float(row['amount'])
                    expense = {
                        'date': row['date'],
                        'category': row['category'],
                        'amount': row['amount'],
                        'description': row['description']
                    }
                    expenses.append(expense)
                else:
                    print(f"Skipping invalid expense record: {row}")
    except FileNotFoundError:
        print("No existing expenses found. Starting fresh.")
    return expenses


# Step 7: Interactive Menu
def main():
    expenses = load_expenses()
    budget = monthly_budget()
    while True:
        print('\nPersonal Expense Tracker')
        print('1. Add Expense')
        print('2. View Expense')
        print('3. Track Budget')
        print('4. Save Expense')
        print('5. Exit')
        option = input("Enter your choice: ")

        if option == '1':
            add_expense(expenses)
        elif option == '2':
            display_record(expenses)
        elif option == '3':
            budget_tracking(expenses, budget)
        elif option == '4':
            save_file(expenses)
        elif option == '5':
            save_file(expenses)
            print("Exiting....")
            break
        else:
            print("Invalid choice, please select a valid option")


# Run the application
if __name__ == "__main__":
    main()
