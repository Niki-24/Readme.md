# Readme.md
# ATM Simulation
### Projec Overview
 An ATM simulation in Python is a program that mimics the functionality of a real Automated Teller Machine (ATM), allowing users to practice banking transactions like withdrawals,
deposits, and balance checks in a safe, virtual environment.
## Purpose:
The Primary goal is to provide a hands-on experience of using and ATM without the need for actual bank accounts.
```
class ATM:
    acc_no = 0
    def __init__ (self,name):
        self.name = name
        self.balance = 0
        self.Create_pin()
        ATM.acc_no += 1
        self.history = []
    def Create_pin(self):
        pin = int(input("enter the pin"))
        re_pin = int(input("enter the re-pin"))
        if pin == re_pin:
            print("pin created successfully")
            self.pin = pin
        else:
            print("pin doesnot macth with previous one!!")
            print("Try again !")
    def deposit (self):
         if self.check_pin():
            amount = int(input("enter the amount you want to deposit"))
            if amount <= 0:
                print("Invalid amount")
            else:
                self.balance += amount
                print(f"  Rs.{amount} have been deposited successfully")
                print(f" Current Balance Rs.{self.balance}/-")
            self.history.append(f" deposited amount : Rs.{amount}/- Cr.")
    def withdraw(self):
        if self.check_pin():
            amount = int(input("enter the withdraw amount: "))
            if amount <=100:
                print("Invalid amount")
            elif amount>=self.balance:
                print("Insufficient amount")
            else:
                self.balance -= amount
                print(f" Rs.{amount} have been withdraw")
                print(f" Your Current Balance is Rs.{self.balance}/-")
            self.history.append(f" withdraw amount: Rs.{amount}/-Dr.")

    
    def check_pin(self):
        trials = 0
        while True:
            trials+=1
            check = int(input("enter the pin "))
            if check == self.pin:
                return True
            elif trials == 3:
                print("Your card is blocked!")
                break
            else:
                print("You have enter incorrect pin")
                print(f"{3-trials} trials left")
    def change_pin(self):
        if self.check_pin():
            self.Create_pin()
            

    def show_history(self):
        if self.check_pin():
            print(f"Name {self.name} AccountNo.:- {ATM.acc_no}")
            for i in self.history:
                print(i)

    def show_balance(self):
        self.check_pin()
        print(f"Current balance is {self.balance}")
        
    def save_data(self):
        if self.check_pin():
            file = open(f"{self.name}.txt","a")
            file.writelines(self.history)
            file.close
            print("Your data store successfully")
 ```
New File at / · Niki-24/Python-code-and-Notes 
