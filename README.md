https://wipro365-my.sharepoint.com/:w:/r/personal/ka20587234_wipro_com/Documents/Document.docx?d=w9e821b2bf5144e418aee245d40d87bcb&csf=1&web=1&e=sNYUbk



banking management microservises

Account service:
create account
close account
update account

Customerservice:
Deposit
moneywithdrawl
check balanec
Loan Sevice:apply for loan& intrest
Close Loan

NotificationService:
Notify everything


Issue cards:credit and debit cards



Services & Interaction

1. Account Service

Owns account data (account number, type, balance, status).

Endpoints:

POST/api/accounts Create account

PUT /api/accounts/{id} Update account

Close account POST /api/accounts/{id}/close

25 :

POST /api/accounts/{id}/adjust

Deposit/Withdraw (amount in request)

GET /api/accounts/{id}/balance Get balance

2. Transaction Service

Handles deposits & withdrawals via Account Service.

Keeps transaction history in its own DB.

Endpoints:

POST/api/transactions/deposit transaction

Call Account Service to deposit, save

POST /api/transactions/withdraw transaction

Call Account Service to withdraw, save

GET /api/transactions/account/{accountId}

List all transactions

3. Loan Service

Owns loan data and interest calculation.

Calls Account Service to credit loan amount and debit repayments.

Endpoints:

POST /api/loans/apply Create loan, credit amount to account

POST/api/loans/{id}/repay

Debit repayment from account

GET /api/loans/{id}/interest

Calculate interest

POST/api/loans/{id}/close

Close loan

4. Card Service

Manages credit/debit card issuance for accounts.

Endpoints:

POST /api/cards/issue

Create card linked to account

POST /api/cards/{id}/block

Block card

POST /api/cards/{id}/close

Close card

5. Notification Service

Stores notification messages in MySQL.

Since no RabbitMQ, other services will call it directly via REST when they need to send a notification.

Endpoints:

POST /api/notifications

Store notification message

GET /api/notifications List notifications
