# AmaapOOMD
---

# Unusual Spends Alert System

## 1)Problem Statement

- You work at a credit card company and as a value-add they want to start providing alerts to users when their spending in any particular category is higher than usual.
- Compare the total amount paid for the current month, grouped by category with the previous month.
- Filter down to the categories for which the user spent at least 50% more this month than last month.
- Compose an e-mail message to the user that lists the categories for which spending was unusually high.

## Classes and Variables

### User:
- States:
  - `userId`: Unique id of the user.
  - `name`: Name of the credit card user.
  - `email`: Email address of the credit card user.
- Constructor:
  - `User(int userId, String name, String email)`
- Behaviour:
  - `getUserId()`: Retrieve the user id of the user.
  - `getName()`: Retrieve the name of the user.
  - `getEmail()`: Retrieve the email address of the user.

### Transaction:
- States:
  - `transactionId`: Unique Id of Transaction.
  - `category`: Category of the transaction (e.g., groceries, travel).
  - `amount`: Amount of transaction.
  - `date`: Date of the transaction.
  - `userId`: User who made the transaction.
- Constructor:
  - `Transaction(int transactionID, String category, int amount, LocalDate transactionDate, int userId)`
- Behaviour:
  - `getTransactionId()`: Retrieve transaction id.
  - `getCategory()`: Retrieve the category of the transaction.
  - `getAmount()`: Retrieve the amount spent in the transaction.
  - `getDate()`: Retrieve the date of the transaction.
  - `getUserId()`: Retrieve the User who made the transaction.

### TransactionHistory:
- States:
  - `transactions`: List of transactions made by the user.
- Behaviour:
  - `addTransaction(Transaction transaction)`: Add a new transaction to the transaction history.
  - `getAllTransactions()`: Retrieve the list of transactions.
  - `filterTransactionByCurrentMonth()`: Filter transactions for the current month.
  - `filterTransactionByPreviousMonth()`: Filter transactions for the previous month.
  - `filterTransactionByCategory(String category)`: Filter transactions by category.
  - `comparePreviousMonthSpending()`: Compare total spending of the current month with the previous month and identify unusual spends.

### ExtraPayUsers:
- States:
  - `userId`: Id of user who is doing extra spent.
  - `category`: On which category they spent.
  - `moreSpentAmount`: How much extra they are paying.
- Behaviour:
  - `getUserId()`: Retrieve Id Of user.
  - `getCategory()`: Retrieve category.
  - `getMoreSpentAmount()`: get Amount Of extra spent.

### UserHandler:
- States:
  - `users`: List of users.
- Behaviour:
  - `addUser(User user)`: Add a new user.
  - `getUserByUserId(int userId)`: Retrieve data of a specific user.



### SendEmail:
- Behaviour:
  - `sendEmail(String subject, String body, String userEmail)`: Send mail to the user.

***
# Election Results


## 2)Problem Statement

---

-It's election night! Exciting! We have a feed of election results from a data supplier. 
They will supply us a file which will be updated throughout the night as results come in.

A result will consist of:
 - A constituency
 - A repeating set of pairs with the party code and the votes cast

So for example:

Banglore, 11014, BJP, 17803, INC, 4923, CPI, 2069, NCP
Pune, INC, 9389, CPI, 4829, BJP, 3375, NCP, 3371, BSP, 309, IND

Party Codes -

BJP - Bhartiya Janta Party
INC - Indian National Congress
BSP - Bahujan Samaj Party
CPI - Communist Party of India
NCP - Nationalist Congress Party
IND - Independant

We want to transform this into a standard result that shows:

- the constituency name
- translates the party code into a full name
- shows the winner of the constituency


## Classes and Variables


### ElectionResult Class

- **States**:
  - `constituency`: String - Represents the name of the constituency.
  - `results`: HashMap<String, Integer> - Represents the results of the election for each party.

- **Constructors**:
  - `ElectionResult(String constituency, HashMap<String, Integer> results)`: Initializes the ElectionResult with the given constituency name and results.

- **Behaviour**:
  - `getWinner()`: Returns the winning party for the constituency.


### ElectionAnalyzer Class

- **States**:
  - `parties`: HashMap<String, Party> - Represents a mapping of party codes to Party objects.
  - `results`: ArrayList<ElectionResult> - Represents the list of election results.

- **Constructors**:
  - `ElectionAnalyzer()`: Empty constructor for analyzer

- **Behaviour**:
  - `processResults(ArrayList<ElectionResult>)`: Reads election results from the list and do the analysis.
  - `displayResults()`: Displays the analyzed results including constituency-wise results and winners.

 ### Party Enum

- **Enum Constants**:
  - `BJP("BJP", "Bhartiya Janta Party")`
  - `INC("INC", "Indian National Congress")`
  - `BSP("BSP", "Bahujan Samaj Party")`
  - `CPI("CPI", "Communist Party of India")`
  - `NCP("NCP", "Nationalist Congress Party")`
  - `IND("IND", "Independent")`
