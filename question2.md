# 4+1 Model - Logical View for Banking Application

```mermaid
classDiagram
    class BankingApp {
        - Customer : Customer
        - Account : Account
        + login()
        + makeDeposit()
        + makeWithdraw()
        + getBalance()
    }

    class Customer {
        - customerId: String
        - name: String
        - accounts: List~Account~
        + login(username: String, password: String): bool
        + makeDeposit(account: Account, amount: float)
        + makeWithdraw(account: Account, amount: float)
        + getBalance(account:Account)
    }

    class Account {
        - accountId: String
        - balance: float
        -transactions: List~Transactions~
        + deposit(amount: float)
        + withdraw(amount: float)
        + getBalance(): float
        
    }

    class Transaction {
        - transactionId: String
        - amount: float
        - date: Date
        +getValues(): values
    }

    BankingApp --> Customer : uses
    Customer --> Account : owns
    Account --> Transaction : makes
    BankingApp --> Account : manages
