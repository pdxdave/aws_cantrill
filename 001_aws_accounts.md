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

## Create IAM identity with Admin permissions
1. In the IAM service, to the right there is the AWS Account.  It has an ID, Alias and URL.
2. If you're going to sign-on with any IAM identity then you need to use a sign-on URL for IAM users. We can create an alias for a more informative sign-on. 
    * click create under Account Alias. Type in a preferred alias. It must be unique to help identify the account you're logging into. 
    * it needs to be globally unique. I made my dm-general-kamaboko
3. Now create a new identity and give it AdministratorAccess. Access Management > Users > Add Users > follow instructions.  Attach existing policy directly to the user. 
4. Make sure everything looks good.  Then copy the customized sign-on-url and save it to a document. We'll copy and paste this in the url to sig-on as the newly created admin user.  Just put in the user name and password.

## IAM Access Keys
1. When logging into the management console you'll either use a username and password (long term credentials), or access keys when using the CLI.
2. Long term credentials must be explicitly changed.
3. !! An IAM user has 1 username and 1 password, BUT...an IAM user can have two access keys.
4. Access keys can be created, deleted, made inactive/active. When created they are defaulted to active.
5. Access keys have two parts: Access Key ID, Secret Access Key
    * The Secret Access Key must be copied the time it was created. AWS will not let you see it again.
    * The Secret Access Key cannot be changed alone. The AK and SAK must be deleted and re-created.
    * "Rotating Access Keys" means to delete existing set and make a new set.
    * The Root User can have them, but it's not recommended.  Usually just for IAM entities. Not Roles.