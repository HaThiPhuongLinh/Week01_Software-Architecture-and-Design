# Software Description Document for ATM System (Automated Teller Machine)
## 1. Introduction
> The software to be designed will control a simulated automated teller machine (ATM) having a 
magnetic stripe reader for reading an cash card, a customer console (keyboard and display) for 
interaction with the customer, a slot for depositing envelopes, a dispenser for cash, a printer for printing customer receipts, and a key-operated switch to allow an operator 
to start or stop the machine. The ATM will communicate with the bank's computer over an 
appropriate communication link.
>
> The ATM will service one customer at a time. A customer will be required to insert an cash card 
and enter a personal identification number (PIN) - both of which will be sent to the bank for 
validation as part of each transaction. The customer will then be able to perform one or more 
transactions. The card will be retained in the machine until the customer indicates that he/she 
desires no further transactions.

### Definitions
+ **Account**: a single account in a bank against which transactions can be applied.
+ **ATM**: A machine that interacts with customers and the bank computer to process transactions and dispense cash.
+ **Bank**: A financial institution that holds accounts and issues cash cards for customers.
+ **Bank computer**: A computer that connects the ATM network and the bank’s cashier stations and verifies transactions.
+ **Cash card**: a card assigned to a bank customer that authorizes access to accounts using an ATM machine. Each card contains a bank code and a card number, coded in accordance with national standards on credit cards and cash cards. The bank code uniquely identifies the bank within the consortium. The card number determines the accounts that the card can access.
+ **Customer**: the holder of one or more accounts in a bank.
## 2. Overall description
### 2.1 Product perspective
 ![image](https://github.com/HaThiPhuongLinh/Week01_Software-Architecture-and-Design/assets/109422010/6a9777dc-f99b-41db-bb24-7ccdc6eca92f)
   - ﻿The ATM network does not work independently. It works together with the banks' computers and the software run by the network's banks.
### 2.2 Product functions
The main functions of the ATM system are:
  - Withdraw cash
  - Deposit cash
  - Transfer funds
  - Check balance
  - Change PIN
### 2.3. User Characteristics
There are several users of the ATM network:
- Customers are simply members of the general public with no special training.
- Bank security personnel need have no special education or experience.
- Maintainers must be experienced network administrators, to be able to connect new ATMs to the network.
### 2.4. General Constraints
- **Regulatory policies**: Ensure adherence to banking, privacy, tax, and anti-money laundering laws, along with compliance with ISO 8583 and EMV standards.
- **Hardware limitations**: Operate within the constraints of physical and technical aspects, addressing size, weight, power, memory, processing speed, and handling hardware failures.
- **Parallel operation**: Support multiple users and transactions, ensuring data consistency, integrity, and providing user feedback in case of delays or failures.
- **Audit functions**: Implement monitoring and recording of activities, generating logs, reports, and statistics for both internal and external purposes.
- **Control functions**: Provide authorized personnel with the ability to manage and configure the system locally and remotely, including parameters and settings adjustments.
- **Criticality of the application**: Prioritize reliability, availability, and security to prevent loss, damage, or theft of data and cash, ensuring user privacy and preventing unauthorized access.
- **Safety and security considerations**: Address physical and electronic safety and security aspects, incorporating features to prevent harm, vandalism, fraud, and utilizing encryption and authentication techniques.
- **Standards**: Conform to software engineering standards such as IEEE, ISO, and CMMI for software requirements, design descriptions, quality, testing, and process improvement.
### 2.5. Assumptions and Dependencies
- Hardware  never fails
- ATM casing is impenetrable
- Limited number of transaction per day (sufficient paper for receipts)
- Limited amount of money withdrawn per day (sufficient money)
## 3. Specific Requirements
### 3.1. External Interfaces
- User Interfaces
  
  ![image](https://github.com/HaThiPhuongLinh/Week01_Software-Architecture-and-Design/assets/109422010/80bf380b-cfe7-432a-a28f-25a727370603)
- Hardware Interfaces
  
  ﻿- The ATM network has to provide hardware interfaces to:
    - Various printers
    - Various ATM machines (There are several companies producing the ATM machines)
    - Several types of networks The exact specification of the hardware interfaces is not part of this document
- Software Interfaces
  
  ﻿- The ATM network has to provide software interfaces to:
    - The software used by different banks
    - Different network software
 
- Communication Interfaces
   - There is no restriction of the ATM network to a specific network protocol as long as the performance requirements are satisfied.
 ### 3.2. Functional Requirements
 #### 3.2.1 Use case diagram
![image](https://github.com/HaThiPhuongLinh/Week01_Software-Architecture-and-Design/assets/109422010/be2aace2-0e9f-4428-9df0-762587754fec)
 - **System Startup Use Case**: The system is started up when the operator turns the operator switch to the "on" position. The operator will be asked to enter the amount of money currently in the cash dispenser, and a connection to the bank will be established. Then the servicing of customers can begin.
 - **System Shutdown Use Case**:  The system is shut down when the operator makes sure that no customer is using the machine, and then turns the operator switch to the "off" position. The connection to the bank will be shut down. Then the operator is free to replenish cash and paper, etc.
 - **Maintenance**: Some practices such as regular cleaning,  software updates, preventative maintenance, monitoring and reporting,..
 - **Session Use Case**:
    - A session is started when a customer inserts an ATM card into the card reader slot of the machine. The ATM pulls the card into the machine and reads it. (If the reader cannot read the card due to improper insertion or a damaged stripe, the card is ejected, an error screen is displayed, and the session is aborted.) The customer is asked to enter his/her PIN, and is then allowed to perform one or more transactions, choosing from a menu of possible types of transaction in each case. After each transaction, the customer is asked whether he/she would like to perform another. When the customer is through performing transactions, the card is ejected from the machine and the session ends. If a transaction is aborted due to too many invalid PIN entries, the session is also aborted, with the card being retained in the machine.
    - The customer may abort the session by pressing the Cancel key when entering a PIN or choosing a transaction type.
 - **Transaction Use Case**:
    - *Note: Transaction is an abstract generalization. Each specific concrete type of transaction implements certain operations in the appropriate way. The flow of events given here describes the behavior common to all types of transaction. The flows of events for the individual types of transaction (withdrawal, deposit, transfer, inquiry) give the features that are specific to that type of transaction.*
      - A transaction use case is started within a session when the customer chooses a transaction type from a menu of options. The customer will be asked to furnish appropriate details (e.g. account(s) involved, amount). The transaction will then be sent to the bank, along with information from the customer's card and the PIN the customer entered.
      - If the bank approves the transaction, any steps needed to complete the transaction (e.g. dispensing cash) will be performed, and then a receipt will be printed. Then the customer will be asked whether he/she wishes to do another transaction.
      - If the bank reports that the customer's PIN is invalid, the Invalid PIN extension will be performed and then an attempt will be made to continue the transaction. If the customer's card is retained due to too many invalid PINs, the transaction will be aborted, and the customer will not be offered the option of doing another.
      - If a transaction is cancelled by the customer, or fails for any reason other than repeated entries of an invalid PIN, a screen will be displayed informing the customer of the reason for the failure of the transaction, and then the customer will be offered the opportunity to do another.
      - The customer may cancel a transaction by pressing the Cancel key as described for each individual type of transaction below.
      - All messages to the bank and responses back are recorded in the ATM's log.
- **Withdrawal Transaction Use Case**:
    - A withdrawal transaction asks the customer to choose a type of account to withdraw from a menu of possible accounts, and to choose an amount from a menu of possible amounts. The system verifies that it has sufficient money on hand to satisfy the request before sending the transaction to the bank. (If not, the customer is informed and asked to enter a different amount.) If the transaction is approved by the bank, the appropriate amount of cash is dispensed by the machine before it issues a receipt. (The dispensing of cash is also recorded in the ATM's log.)
    - A withdrawal transaction can be cancelled by the customer pressing the Cancel key any time prior to choosing the amount.
- **Deposit Transaction Use Case**:
    - A deposit transaction asks the customer to choose a type of account to deposit to from a menu of possible accounts, and to type in an amount on the keyboard. The transaction is initially sent to the bank to verify that the ATM can accept a deposit from this customer to this account. If the transaction is approved, the machine accepts an envelope from the customer containing cash and/or checks before it issues a receipt. Once the deposit has been received, a second message is sent to the bank, to confirm that the bank can credit the customer's account - contingent on manual verification of the deposit contents by an operator later. 
    - A deposit transaction can be cancelled by the customer pressing the Cancel key any time prior to inserting the deposit. The transaction is automatically cancelled if the customer fails to insert the deposit within a reasonable period of time after being asked to do so.
- **Transfer Transaction Use Case**:
    - A transfer transaction asks the customer to choose a type of account to transfer from a menu of possible accounts, to choose a different account to transfer to, and to type in an amount on the keyboard. No further action is required once the transaction is approved by the bank before printing the receipt. 
    - A transfer transaction can be cancelled by the customer pressing the Cancel key any time prior to entering an amount.
- **Inquiry Transaction Use Case**:
    - An inquiry transaction asks the customer to choose a type of account to inquire about from a menu of possible accounts. No further action is required once the transaction is approved by the bank before printing the receipt.
    - An inquiry transaction can be cancelled by the customer pressing the Cancel key any time prior to choosing the account to inquire about.
- **Invalid PIN Extension**:
    - An invalid PIN extension is started from within a transaction when the bank reports that the customer's transaction is disapproved due to an invalid PIN. The customer is required to re-enter the PIN and the original request is sent to the bank again. If the bank now approves the transaction, or disapproves it for some other reason, the original use case is continued; otherwise the process of re-entering the PIN is repeated. Once the PIN is successfully re-entered, it is used for both the current transaction and all subsequent transactions in the session. If the customer fails three times to enter the correct PIN, the card is permanently retained, a screen is displayed informing the customer of this and suggesting he/she contact the bank, and the entire customer session is aborted.
    - If the customer presses Cancel instead of re-entering a PIN, the original transaction is cancelled.
