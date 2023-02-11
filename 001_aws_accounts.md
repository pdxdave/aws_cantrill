# AWS Accounts

## What is an AWS account?
It is a container for identities (e.g., users) and resources.
Create accounts for specific uses (e.g., test, dev, production)    
An account has...
1. an account name
2. a unique email address - tied to account ROOT user
    * Root user cannot be restricted
3. a credit card
4. by default all access is denied except for root user

## ... vs Users, Groups, and Roles
1. Identity Access Management (IAM) creates users, groups, roles
2. they can be given full or limited permissions
    * all users, groups, roles start with no permissions

## MFA - multi factor authentication
1. By default single factor/one factor is used (username, password)
2. MFA can be used on a key fob (generates codes), or virtual device added to apps like Authy accessed on your phone
3. Activate MFA for a specific user 
4. Upon login AWS gens a secret key (& additional info tied to key), which needs to be input to an authenticator.
    * AWS can create a QR code based on above info.
    * It's scanned into the phone, app displays a new code
    * The app can hold one or more virtual MFAs 
    * This code is then entered into the AWS sign on for verification

## Setting up MFA for the root user
1. Log in as the root user, select user at top right of page and take Security credentials. 
2. Activate MFA.  Three options appear: virtual mfa device (e.g., software), u2f security key (e.g., yubikey), other hardware device (e.g., gemalto token)
3. I used Twilio Authenticator software solution.

## Billing
1. To view billing overview, as the root user go to top right of screen, dropdown root user name and take Billing Dashboard
2. View monthly bills
    * Select Bills. A monthly dropdown appears outlining all of the AWS Service Charges
3. Setup Billing Preferences
    * Select receive pdf invoice my email and receive free tier usage alerts.  Assign to an email.
4. Setup a Budget
    * First go to Cost Explorer. 
    * Go to Budgets and Create budget
    * There are different kinds of budgets: cost, usage, savings, reservation. We'll make a Cost budget.
    
