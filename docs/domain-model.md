# FleetFlow Domain Model

## User

Represents a person using the system.

Fields:

* Id
* Name
* Email
* PasswordHash
* Role
* CreatedAt

Roles:

* Customer
* Restaurant
* Rider
* Admin

---

## Restaurant

Represents a restaurant registered in the platform.

Fields:

* Id
* Name
* Status
* CreatedAt

Relationships:

* Has many MenuItems
* Has many Orders

---

## MenuItem

Represents a food item available for ordering.

Fields:

* Id
* RestaurantId
* Name
* Description
* Price
* IsAvailable

Relationships:

* Belongs to Restaurant

---

## Rider

Represents a delivery rider.

Fields:

* Id
* Name
* AvailabilityStatus
* CurrentLatitude
* CurrentLongitude

Relationships:

* Can have many Assignments

---

## Order

Represents a customer order.

Fields:

* Id
* CustomerId
* RestaurantId
* AssignedRiderId
* Status
* TotalAmount
* CreatedAt

Relationships:

* Belongs to Customer
* Belongs to Restaurant
* May belong to Rider
* Has many OrderItems

---

## OrderItem

Represents an item within an order.

Fields:

* Id
* OrderId
* MenuItemId
* Quantity
* UnitPrice

Relationships:

* Belongs to Order
* References MenuItem

---

## Assignment

Represents rider allocation to an order.

Fields:

* Id
* OrderId
* RiderId
* AssignedAt
* Status

Relationships:

* Belongs to Rider
* Belongs to Order

---

## Order Status Flow

Created

↓

Accepted

↓

Preparing

↓

ReadyForPickup

↓

AssignedToRider

↓

PickedUp

↓

Delivered

Possible terminal state:

Cancelled
