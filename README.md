## TO DO

## Plan

## Issues/questions:
- Is there a limit for how many accounts can be created
- Are transactions fully internal
- What does "a from account and a to account" mean?
- Are there max lengths for email/password in the login screen?

## Task
- What a user should see and/or do? - State Transition Table
- What inputs, user interactions, actions can be taken and effects those may have? - State Transition Table
- What a user should/must not see or be able to? - Make notes of edge cases/undesired functionality
- What sorts of things it might mean from an implementation point of view?
- Any assumptions you're having to make?
- Any clarifying questions you might want to ask of whoever wrote the material?

## BANK-01	
User can enter username and password into a login page to log in to the banking application

- User should see username and password fields, and be able to input text into them
- User should be able to press 'Login', to log in to account with same details
- Inputs should have a maximum length, to avoid typing unnecessarily long incorrect details
- If either field is empty, there should be an error message, without making an attempt to actually login somewhere
- Users shouldn't be able to bypass Login screen, and see accounts, without logging in
- Successfully logging in will change the page
- Users should get an error message if they input incorrect details, and stay on the same page
- Assumptions: user details are stored securely in a database/server. Assuming also that passwords and emails have been validated before registration, with restrictions e.g. special chars
- Questions: what is the username? Is it linked to the email address? Can you use the email as a username?
- Was there any email verification at all? Where the user clicks a link from an email
- Is there 2 Factor Authentication? This would be a lot more secure than username and password

## BANK-02	
User can view all of their accounts in one page

- User can see their username correctly displayed at the top, and 'Makers Bank'
- User should be able to see all of their accounts, correctly named, and be able to click on them
- User should not be able to see anybody else's accounts apart from their own
- If there are more accounts than can fit on the page, the user can scroll down to see rest of their accounts
- If there are more accounts than can fit on the page, the setup transaction button is still visible
- Clicking on an account will display details about that account, on a new page
- Clicking 'setup transaction' will prompt the user to setup a transaction, on a new page
- Assumptions: accounts are stored securely in a database/server
- Questions: is there a limit for how many accounts can be created?

## BANK-03	
User can view details of a single account, including balance and transaction history
- Makers Bank title visible as per wireframe
- The account number that the user just clicked appears at the top of the page
- The user can clearly see the balance of the account, correctly formatted and in the right currency
- In general, the balance and transaction history are familiar to the user, based on their memory of recent transactions 
- User can scroll down to read further into their transaction history
- Back button takes user back to previous screen (Accounts)
- Assumptions: the information is up to date and can be different every time user spends money and opens it. Information must be stored securely in database, and is fetched when user opens page
- Questions: is there more detail that could be added to each transaction (e.g. balance at the time of the transaction). 
- Can you click on each transaction to show more information, e.g. time, recipient, location of transaction?
- Could debit transactions be in red and credit transactions be in green?
- Could the user filter between credit transactions and debit transactions?
- Could credit/debit be reformatted as:
'+£200'/'-£200', much more simple

## BANK-04	
A transaction page allows a user to specify an amount of money, from one account to another
- Makers Bank title visible as per wireframe
- Displays 'transaction for' then the correct username
- Input fields are selectable. They automatically prompt the correct keyboard type (the number pad shows up). 
- Account numbers are automatically hyphenated so that the user can just input numbers. Letters/special chars shouldn't be allowed to be inputted. 
- Amount to be transferred should automatically start with a £ sign
- If the user inputs an account number that is invalid, an error message is displayed. Could the 'select account' feature be a drop down menu of all of the users accounts? Prevents potential incorrect account number
- If the user inputs more money than is in the chosen account, a message is displayed saying 'insufficient funds', and doesn't allow them to submit transaction
- No back button. There should be one to allow user to return if they didn't mean to press 'setup transaction'
- No need to input PIN number. There should be this extra level of security to protect people who have leaked their email/password
- If user presses 'accept', it will prompt an 'are you sure' message. This could show the user the impact of the transaction (projected account balances). Then if user confirms, a confirmation message that the money has been sent
- User returns to accounts page after making transaction, as per wireframe
- Assumptions: all transactions are internal to the user
- Questions: is there a limit for an amount of money that can be transferred?

## BANK-05	
A transaction causes an amount of money to move from one account to another, altering both account balances appropriately

- User can click on the two accounts that were involved in the transaction, see a correct credit/debit in the transaction history, with the transaction reflected in the new account balance
- Assumptions: balance/transactions are accurate and actually updated in the bank's database, not just changed client side. One source of truth - the database
- Questions: are transactions instant or will there be a delay?

## Focusses for quality and risks
App currently only supports internal transactions. Does this mean the security risks are less severe?
- Security and risk prevention is the number one priority for quality. Security is assumed by the user. Significant overlap
- Security - details must be encrypted and stored securely to prevent malicious acts. (Server side security) 
- Business can lose reputation if there are security breaches. Lack of authentication allows people to steal money. In its current form, someone can guess a password and get total access to every account. 2 Factor Authentication is a must, and a PIN when making a transaction. (Client side security)
- Information must be up to date and accurate. One source of truth. So that users aren't spending imaginary money, and your bank balance can't just randomly disappear/fall due to a bug
- An app that is hard to use will cause customers to potentially move to another bank. A high quality app, with a smooth UI (add back buttons) will attract users
- Users should be able to see as much information as possible, e.g. transaction details. This information isn't in the current plan for the app, but it would increase security because users could more easily spot suspicious transactions
