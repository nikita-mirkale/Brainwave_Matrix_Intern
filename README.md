class ATM:
    def __init__(self):
        self.balance = 0
        self.pin = "1234"
        self.transaction_history = []

    def login(self):
        attempts = 3
        while attempts > 0:
            entered_pin = input("Enter your PIN: ")
            if entered_pin == self.pin:
                print("Login successful!")
                return True
            else:
                attempts -= 1
                print(f"Incorrect PIN. You have {attempts} attempts left.")
        print("Too many failed attempts. Exiting.")
        return False

    def check_balance(self):
        print(f"Your current balance is: ₹{self.balance}")

    def deposit(self):
        amount = float(input("Enter amount to deposit: ₹"))
        if amount > 0:
            self.balance += amount
            self.transaction_history.append(f"Deposited: ₹{amount}")
            print(f"₹{amount} deposited successfully.")
        else:
            print("Invalid deposit amount.")

    def withdraw(self):
        amount = float(input("Enter amount to withdraw: ₹"))
        if 0 < amount <= self.balance:
            self.balance -= amount
            self.transaction_history.append(f"Withdrew: ₹{amount}")
            print(f"₹{amount} withdrawn successfully.")
        else:
            print("Insufficient balance or invalid amount.")

    def view_transaction_history(self):
        if self.transaction_history:
            print("Transaction History:")
            for transaction in self.transaction_history:
                print(transaction)
        else:
            print("No transactions yet.")

    def start(self):
        print("*"*89)
        print(f"{" "*40} WELCOME TO ATM !")
        print("*"*89)
        if not self.login():
            return

        while True:
            print("\nATM Menu:")
            print("1. Check Balance")
            print("2. Deposit Money")
            print("3. Withdraw Money")
            print("4. View Transaction History")
            print("5. Exit")
            
            choice = input("Choose an option (1-5): ")
            
            if choice == "1":
                self.check_balance()
            elif choice == "2":
                self.deposit()
            elif choice == "3":
                self.withdraw()
            elif choice == "4":
                self.view_transaction_history()
            elif choice == "5":
                print("Thank you for using the ATM. Goodbye!")
                break
            else:
                print("Invalid option. Please try again.")

# Instantiate and start the ATM
atm = ATM()
atm.start()
