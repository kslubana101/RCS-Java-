# Shipping Cost Calculator (Java)

## Overview
This project is a Java-based shipping cost calculator developed as part of **COE318 – Software Systems** at **Toronto Metropolitan University**.  
It computes delivery costs for different parcel types based on weight, distance, insurance, delivery speed, size handling, and international customs fees.

The project demonstrates **object-oriented programming**, including inheritance, method overriding, input validation, and exception handling.

---

## Features
- Calculates shipping costs for standard, express, and international deliveries  
- Supports optional insurance with flat-rate or percentage-based fees  
- Applies size-based handling surcharges  
- Includes express delivery premiums and same-day delivery fees  
- Handles international cross-border and customs charges  
- Enforces valid input using exception handling  

---

## Technologies Used
- **Language:** Java  
- **Concepts:**  
  - Object-Oriented Programming (OOP)  
  - Inheritance and polymorphism  
  - Method overriding  
  - Exception handling  
  - Modular design  

---

## Source Code

### Parcel.java
```java
/**
 * Base class representing a parcel shipment.
 */
public class Parcel {

    protected double weight;
    protected double distance;
    protected boolean insured;

    public Parcel(double weight, double distance, boolean insured) {
        if (weight <= 0) {
            throw new IllegalArgumentException("Weight must be positive");
        }
        if (distance < 0) {
            throw new IllegalArgumentException("Distance cannot be negative");
        }

        this.weight = weight;
        this.distance = distance;
        this.insured = insured;
    }

    public double shippingCost() {
        double cost = 3.00 + (0.50 * weight) + (0.10 * distance);

        if (insured) {
            double insuranceFee = Math.max(1.50, 0.02 * cost);
            cost += insuranceFee;
        }

        return cost;
    }
}


