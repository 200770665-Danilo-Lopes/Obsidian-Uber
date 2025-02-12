
# Ride Tracking Feature

## Description

A user must be able to see trip details in real-time and should be able to
share information about it with other contacts from personal phone's address book.

## Page

**Track your Ride** (`/features/ride_tracking/:id`)

## User Story

```
As an Uber user
I want to track my ride in real-time
So that I can monitor my journey and estimated arrival time
```

## Acceptance Criteria

```
Given I am in an active ride
And my internet connection is stable
```

## Feature: Ride Tracking


```
@live-tracking 
Scenario: Track driver location in real-time
  When I view the tracking screen
  Then I should see:
    | driver's current location      |
    | my current location            |
    | destination                    |
    | optimal route                  |
    | estimated time of arrival      |
  And the map should update every 3 seconds
  And I should see the remaining distance
```


```
@share-trip 
Scenario: Share trip details with contacts
  When I tap "Share Trip Status"
  And I select a contact from my list
  Then my contact should receive a link to track my ride
  And they should see my real-time location
  And they should see my estimated time of arrival
```

 
```
@route-change
Scenario: Driver takes alternate route
  When the driver deviates from suggested route
  Then the ETA should be recalculated
  And I should see the updated route on the map
  And I should see the new estimated time of arrival
```