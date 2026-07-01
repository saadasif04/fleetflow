# FleetFlow Event Flow

## Event-Driven Architecture

Services communicate through events using RabbitMQ.

The service that creates the event is called the publisher.

Services reacting to the event are consumers.

---

## OrderCreated

Publisher:

* Order Service

Consumers:

* Notification Service
* Delivery Service

Purpose:

* Notify restaurant
* Begin rider assignment process

---

## OrderAccepted

Publisher:

* Order Service

Consumers:

* Notification Service

Purpose:

* Inform customer that restaurant accepted the order

---

## OrderReadyForPickup

Publisher:

* Order Service

Consumers:

* Delivery Service
* Notification Service

Purpose:

* Trigger rider assignment
* Inform customer

---

## RiderAssigned

Publisher:

* Delivery Service

Consumers:

* Notification Service
* Order Service

Purpose:

* Update order status
* Inform rider and customer

---

## OrderPickedUp

Publisher:

* Delivery Service

Consumers:

* Notification Service

Purpose:

* Inform customer that delivery is in progress

---

## OrderDelivered

Publisher:

* Delivery Service

Consumers:

* Notification Service

Purpose:

* Complete order lifecycle
* Inform customer

---

## Future Events

* RiderLocationUpdated
* OrderCancelled
* RestaurantOffline
* RiderUnavailable
* PaymentCompleted
* PaymentFailed
