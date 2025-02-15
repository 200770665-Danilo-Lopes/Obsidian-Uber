
## Uber Onboarding Flow Features

### Description

Uber Onboarding Flow guides new users through account creation or login, verification, and 
acceptance of terms before accessing the main app screen for ride or food ordering.
(Available on: https://mobbin.com/flows/3fe8ec28-3104-4ad4-a8fd-6067ed54d533?tab=screens&scrollToScreenIndex=3)

### Page

**Sign-Up** (`/features/register/:id`)

### User Story
```
As a potential user
I want to be able to Sign Up  
So that I can use the service
```

## Acceptance Criteria

```
Given the user has installed the Uber app on their device
```

### Feature: Register

```
@onboarding-sucessful
  Scenario: Sucessful Onboarding
    When the user opens the Uber app
    Then the app displays a welcome screen with an illustration and a "Get started" button

  @account_creation
    Scenario: Creating a New Uber Account
      Given the user is on the welcome screen
      When the user taps the "Get started" button
      Then the app prompts the user to enter their mobile phone number
      When the user enters a valid mobile phone number
      Then the app sends a verification code via SMS
      When the user enters the correct verification code
      Then the app prompts the user to enter personal details, including:
        | Full Name |
        | Email Address |
        | Password |
      When the user provides the required information
      Then the app creates a new account and displays the terms and conditions
      When the user accepts the terms and conditions
      Then the app proceeds to the main screen, ready for service selection

  @login
    Scenario: Logging into an Existing Uber Account
      Given the user is on the welcome screen
      When the user taps the "Sign In" option
      Then the app prompts the user to enter their registered mobile phone number or email address
      When the user enters valid credentials
      Then the app sends a verification code via SMS or email
      When the user enters the correct verification code
      Then the app displays the terms and conditions
      When the user accepts the terms and conditions
      Then the app proceeds to the main screen, ready for service selection
  
  @permissions
    Scenario: Granting Necessary Permissions
      Given the user has logged into their account
      When the app requests location access permission
      And the user grants location access
      Then the app requests notification permission
      When the user grants notification permission
      Then the app confirms all necessary permissions are granted
  
  @main_interface
    Scenario: Accessing the Main Interface
      Given the user has completed account setup and granted necessary permissions
      When the app displays the main screen
      Then the user can choose between ride services or food ordering
      And the app is ready to accept user requests

@onboarding-fail

  Scenario: Failed Onboarding Due to Invalid Phone Number
    Given the user has launched the Uber app for the first time  
    When the user taps the "Get Started" button
    And enters an invalid phone number  
    Then the user should receive an error message indicating the phone number is invalid  
    And the user should be prompted to enter a valid phone number

  Scenario: Failed Onboarding Due to Incorrect Verification Code
    Given the user has entered a valid phone number  
    When the user enters an incorrect verification code  
    Then the user should receive an error message indicating the code is incorrect
    And the user should be prompted to re-enter the verification code

  Scenario: Failed Onboarding Due to Declined Terms and Conditions
    Given the user has completed phone number verification  
    When the user declines the terms and conditions  
    Then the user should be informed that acceptance of the terms is required to use the app  
    And the user should be prompted to accept the terms and conditions to proceed
            


```

