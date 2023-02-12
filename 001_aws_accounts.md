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
    * Name the budget, set amount to monthly, recurring, fixed, and enter an amount.
    * Next screen set an alert budget threshold.
5. !!! In root user, go to Accounts, scroll down and enable IAM User and Role Access to Billing Info.


## IAM Basics
1. The root user is created with the AWS account.  In affect, they are the same: account and root user.
2. New users should be given ```least privileged access```.  Only what they need.
3. Every AWS account comes with its own IAM database. IAM is GLOBAL, so it is secure against all regions.
4. IAM allows for the creation of three different identity types: User, Group, Roles.
5. Roles can be used by AWS Services, or for granting external access to your account.  Roles are generally used when you want to grant access to services in your acct to an uncertain number of entities.
6. Policies on their own do nothing. They only allow or deny AWS services when attached to a User, Group or Role.
7. IAM has 3 main roles
    * It's an ID provider. Create, modify, delete identities
    * It authenticates the identities (name, password)
    * Once authorized it allows or denies access to resources
8. IAM is no cost, it's Global, only controls its identites, has no direct control on external accts or users
9. It allows use of identity federation (e.g., facebook, google) and use them indirectly to access AWS resources.
