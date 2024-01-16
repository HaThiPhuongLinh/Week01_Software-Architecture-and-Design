# Software Description Document for ATM System (Automated Teller Machine)
## 1. Introduction
> The software to be designed will control a simulated automated teller machine (ATM) having a 
magnetic stripe reader for reading an ATM card, a customer console (keyboard and display) for 
interaction with the customer, a slot for depositing envelopes, a dispenser for cash, a printer for printing customer receipts, and a key-operated switch to allow an operator 
to start or stop the machine. The ATM will communicate with the bank's computer over an 
appropriate communication link.
>
> The ATM will service one customer at a time. A customer will be required to insert an ATM card 
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
+ **Customer**: the holder of one or more accounts in a bank.'
## 2. Overall description
### 2.1 Product perspective
 ![image](https://github.com/HaThiPhuongLinh/Week01_Software-Architecture-and-Design/assets/109422010/6a9777dc-f99b-41db-bb24-7ccdc6eca92f)
   - ﻿The ATM network does not work independently. It works together with the banks' computers and the software run by the network's banks.
### 2.2 Product perspective
   - The ATM network doesn't work independently. It has to work together with the comput- ers/software owned by banks. There are clearly defined interfaces for the different systems.
