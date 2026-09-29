# ============================================
# PERSONAL FINANCE & BUDGET ANALYZER
# ============================================

print("=" * 50)
print("       PERSONAL FINANCE & BUDGET ANALYZER")
print("=" * 50)

# ---------------- INPUT ----------------

income = float(input("\nEnter your monthly income (Rs): "))

rent = float(input("Enter your rent (Rs): "))
uti = float(input("Enter your utilities expense (Rs): "))
groc = float(input("Enter your groceries expense (Rs): "))
gas = float(input("Enter your gas/transport expense (Rs): "))
din = float(input("Enter your dining out expense (Rs): "))
sub = float(input("Enter your subscriptions expense (Rs): "))

# ---------------- EXPENSE DATA ----------------

expenses = [
    ("Rent", rent, "Need"),
    ("Utilities", uti, "Need"),
    ("Groceries", groc, "Need"),
    ("Gas/Transport", gas, "Need"),
    ("Dining Out", din, "Want"),
    ("Subscriptions", sub, "Want")
]

# ---------------- CALCULATIONS ----------------

total_spent = 0

for item in expenses:
    total_spent += item[1]

money_left = income - total_spent

if income > 0:
    savings_percentage = (money_left / income) * 100
else:
    savings_percentage = 0

spending_percentage = (total_spent / income) * 100 if income > 0 else 0

# ---------------- NEEDS & WANTS ----------------

needs = rent + uti + groc + gas
wants = din + sub

# ---------------- BIGGEST EXPENSE ----------------

biggest_expense = max(expenses, key=lambda x: x[1])

# ---------------- BUDGET HEALTH ----------------

if savings_percentage >= 20:
    health = "Excellent"
elif savings_percentage >= 10:
    health = "Good"
elif savings_percentage > 0:
    health = "Needs Improvement"
else:
    health = "Critical"

# ---------------- SUMMARY ----------------

print("\n" + "=" * 50)
print("                 BUDGET SUMMARY")
print("=" * 50)

print(f"Income              : Rs {income:,.2f}")
print(f"Total Spent         : Rs {total_spent:,.2f}")
print(f"Money Left          : Rs {money_left:,.2f}")
print(f"Spending Percentage : {spending_percentage:.1f}%")
print(f"Savings Percentage  : {savings_percentage:.1f}%")
print(f"Budget Health       : {health}")

# ---------------- SPENDING BREAKDOWN ----------------

print("\n" + "=" * 50)
print("              SPENDING BREAKDOWN")
print("=" * 50)

for name, amount, category in expenses:

    percentage = (amount / income) * 100 if income > 0 else 0

    print(
        f"{name:<18} Rs {amount:>10,.2f}   "
        f"{percentage:>5.1f}%   {category}"
    )

# ---------------- NEEDS VS WANTS ----------------

print("\n" + "=" * 50)
print("                NEEDS vs WANTS")
print("=" * 50)

print(f"Essential Needs : Rs {needs:,.2f}")
print(f"Wants           : Rs {wants:,.2f}")

if income > 0:
    print(f"Needs           : {(needs / income) * 100:.1f}% of income")
    print(f"Wants           : {(wants / income) * 100:.1f}% of income")

# ---------------- BIGGEST EXPENSE ----------------

print("\n" + "=" * 50)
print("               BIGGEST EXPENSE")
print("=" * 50)

print(
    f"{biggest_expense[0]}: "
    f"Rs {biggest_expense[1]:,.2f}"
)

# ---------------- INSIGHTS ----------------

print("\n" + "=" * 50)
print("                  INSIGHTS")
print("=" * 50)

if savings_percentage >= 20:
    print("✓ Excellent! You are saving at least 20% of your income.")

elif savings_percentage >= 10:
    print("✓ You are saving money, but there is room for improvement.")

elif savings_percentage > 0:
    print("! Your savings are quite low. Try reducing unnecessary expenses.")

else:
    print("X WARNING: You are spending more than your income.")

# Wants warning

if income > 0 and (wants / income) * 100 > 20:
    print("! Your wants are taking up more than 20% of your income.")

# Dining warning

if income > 0 and (din / income) * 100 > 10:
    print("! Dining out is a significant part of your spending.")

# Subscription warning

if income > 0 and (sub / income) * 100 > 5:
    print("! Consider reviewing your subscriptions.")

# ---------------- SAVINGS TARGET ----------------

print("\n" + "=" * 50)
print("                SAVINGS TARGET")
print("=" * 50)

target = income * 0.20

print(f"Recommended 20% savings : Rs {target:,.2f}")

if money_left >= target:
    print("✓ You have reached the recommended savings target!")
else:
    difference = target - money_left
    print(f"! Try saving another Rs {difference:,.2f}.")

# ---------------- FINAL MESSAGE ----------------

print("\n" + "=" * 50)
print("              FINANCIAL REPORT COMPLETE")
print("=" * 50)

print("\nThank you for using the Personal Finance & Budget Analyzer!")
