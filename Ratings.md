
## Driver and Passenger Rating Feature


### Description

A user must be able to rate the experience using a 1 to 5 stars scale and can provide written feedback with comments upon rating a completed ride.

### Page

**Rate Trip** (`/features/rate_your_trip/:id`)

### User Story
```
As an Uber user
I want to rate my experience
So that I can provide honest feedback, contributing to maintain service quality
```

### Acceptance Criteria

```
Given I have completed a trip
And the payment has been processed
```

## Feature: Driver and Passenger Rating

### Passenger rates driver
```
@rate-driver
Scenario: Passenger rates driver after route completion
  When I am prompted to rate the driver
  And I select correspondent number of stars
  And I select none, one or more reasons

  Examples:
    | Clean Car     |
    | Safe Driving  |
    | Professional  |
    | Polite        |
    | Punctual      |
  
  And I leave a comment or not
  And I press "Submit" button
  Then my rating should be submitted
  And it should affect the driver's overall rating
  And I should see a message after submitting it
```

### Driver rates passenger
```
@rate-passenger
Scenario: Driver rates passenger
  Given I am a driver
  When I finish a trip
  And I select correspondent number of stars
  Then the rating should be submitted
  And it should affect the passenger's overall rating
  And I should be ready to accept new rides
  ```