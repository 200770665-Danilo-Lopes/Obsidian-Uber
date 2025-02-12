
# Ride Booking Feature

## Description

A user can request a ride upon providing valid pickup and dropoff locations.

## Page

**Book a Ride** (`/features/book_a_ride/:id`)

## User Story
```
As an Uber user
I want to request a ride to my destination
So that I can travel conveniently
```

## Acceptance Criteria
```
Given I have a phone with fully functional network conditions
And my location services are enabled
And I have at least one valid payment method
```

## Feature: Ride Booking

```
  @location
  Scenario: Book ride with current location
    When I open the ride requesting screen
    And my current location is automatically detected
    And I enter a valid address as my destination
    Then I should see estimated fare prices for different vehicle types
    And I should see the estimated time of arrival at destination

  @ride-types
  Scenario Outline: Select different ride types
    Given I have entered my pickup and drop-off locations
    When I select "<ride_type>" as my ride option
    Then I should see the updated price estimate
    And I should see the estimated pickup time
    And I should see the car types available

    Examples:
      | ride_type  |
      | UberX      |
      | Comfort    |
      | Black      |
      | XL         |

  @scheduled-ride
  Scenario: Schedule a future ride
    When I tap "Schedule" instead of "Request now"
    And I confirm <date> and <schedule>
    And I enter a valid address as my pickup location
    And I enter a valid address as my destination
    Then my ride should be scheduled for <date> at <schedule>
    And I should receive a confirmation notification
    And I should see the upcoming trip in my scheduled rides list
```