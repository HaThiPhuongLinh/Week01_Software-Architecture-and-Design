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
