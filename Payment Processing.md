
## Payment Processing Feature


### Description

Payments need to be processed automatically when applicable, and the 
user must be able to select a different payment method when needed.

### Page

**Payment Select** (`/features/payment/:id`)

### User Story

```
As an Uber user
Whenever I need to request a ride, I expect it to be available
I want to pay for the service through secure methods
So that I can complete my trip to my destination
```

### Acceptance Criteria

```
Given I have completed my user profile
And I have registered a valid payment method
And I have requested a ride
And a driver has accepted it
```

## Feature: Payment Processing

```
@automatic-payment
Scenario: Automatic payment after route completion
  When the driver arrives at final destination
  Then the total should be automatically calculated 
  And payment should be processed using default payment method
  And I should receive a receipt via email
```

```
@payment-methods
Scenario Outline: Select different payment methods
  When I need to select "<payment_method>" before requesting a ride 
  Then a list of available options should be presented:  
  
  Examples:
  | Bank Account |
  |     Cash     |
  |     PIX      |
  |  Credit Card | 
  
  And I select one of them
  Then the fare should be charged to selected "<payment_method>"
  And I should see the payment confirmation
  And the driver should receive the payment
  And I should receive a receipt via email
```