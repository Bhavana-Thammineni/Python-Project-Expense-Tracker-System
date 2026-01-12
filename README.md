# Python-Project-Expense-Tracker-System
Expense Tracker System

expenses = []

def add_expense():
    amount = float(input("Enter amount: "))
    category = input("Enter category (Food/Travel/Others): ")
    description = input("Enter description: ")
    
    expenses.append({
        "amount": amount,
        "category": category,
        "description": description
    })
    
    print("Expense added successfully!\n")

def view_expenses():
    if not expenses:
        print("No expenses recorded.\n")
        return
    
    print("\nAll Expenses:")
    for i, exp in enumerate(expenses, start=1):
        print(f"{i}. {exp['category']} - {exp['amount']} ({exp['description']})")

def total_expense():
    total = sum(exp["amount"] for exp in expenses)
    print("Total Expense:", total)

def category_summary():
    summary = {}
    for exp in expenses:
        summary[exp["category"]] = summary.get(exp["category"], 0) + exp["amount"]
    
    print("\nCategory-wise Expense:")
    for cat, amt in summary.items():
        print(cat, ":", amt)

while True:
    print("\n1. Add Expense")
    print("2. View Expenses")
    print("3. Total Expense")
    print("4. Category Summary")
    print("5. Exit")
    
    choice = input("Enter choice: ")
    
    if choice == "1":
        add_expense()
    elif choice == "2":
        view_expenses()
    elif choice == "3":
        total_expense()
    elif choice == "4":
        category_summary()
    elif choice == "5":
        print("Thank you!")
        break
    else:
        print("Invalid choice")
