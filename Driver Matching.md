
## Driver Matching Feature

### Description

A passenger will have a request accepted after an available driver is found.

### Page

**Driver Search** (`/features/search_driver/:id`)

### User Story
```
As an Uber user
I want to be matched with the most suitable driver
So that I can get to my destination efficiently
```

## Acceptance Criteria

```
Given I have requested a ride
And there are active drivers in my area
```

### Feature: Driver Matching

```
@matching-criteria
Scenario: Match with nearest available driver
  When the system searches for drivers
  Then it should consider the following factors:
    | distance        |
    | rating          |
    | vehicle type    |
  
  And I should be matched with a driver within 5 minutes
  And I should see the driver's details:
    | name           |
    | photo          |
    | car model      |
    | license plate  |
```


```
@driver-acceptance
Scenario: Driver accepts a new request
  When a nearby driver is found
  Then I should receive a notification
  And I should see the driver's current location on the map
  And I should see the estimated time of pickup
```


```
@driver-decline
Scenario: Driver declines a new request
  When the matched driver declines my request
  Then the system should immediately search for another driver
  And I should be notified that a new driver is being found
  And my estimated pickup time should be updated
```