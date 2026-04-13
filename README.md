# Retail Ordering System

[![Run on JDoodle](https://img.shields.io/badge/Run%20on-JDoodle-blue?style=for-the-badge&logo=java)](https://www.jdoodle.com/ga/vG1glE1maTfqItl7XS%2Fdsg%3D%3D)

Console-based retail ordering system built using Java. Built to demonstrate understanding of Object-Oriented Programming concepts including abstraction, inheritance, composition, encapsulation, and polymorphism.

## Case Scenario

A retail ordering system manages customer purchases through secured customer accounts. A customer account must exist before any transaction can be created, and each transaction exists only under its corresponding account. Every transaction may contain multiple ordered items, each with a quantity and unit price used for subtotal computation.

The system supports two customer classifications: Regular and VIP. Regular customers follow standard pricing computation, while VIP customers receive an additional benefit in the form of a computation factor applied after the transaction subtotal is computed. This factor reduces the final payable amount based on customer type.

Each customer performs two transactions, and each transaction includes multiple items. All computations are handled per transaction: item subtotal, transaction subtotal, and final amount after applying the customer-type factor.

For reporting, all Regular customers are displayed first, followed by VIP customers. Each output includes transaction breakdowns, itemized purchases, subtotal, applied factor, and final amount.

## Features

- Two customer classifications: Regular (×1.00) and VIP (×0.85)
- Multi-item transactions per customer
- Automatic subtotal and final amount computation per transaction
- Computation factor applied based on customer type
- Itemized transaction breakdown in output
- Regular customers displayed before VIP customers
- Clean OOP design using abstract classes and nested inner classes

## Project Structure

```
retail-ordering-system/
├── Customer.java          # Abstract base class with nested Transaction and OrderedItem classes
├── RegularCustomer.java   # Extends Customer, computation factor 1.00
├── VIPCustomer.java       # Extends Customer, computation factor 0.85
└── Main.java              # Application entry point with test cases
```

## Class Descriptions

### Customer *(abstract)*
Abstract base class representing a customer account. Contains the customer's name, type, and a list of transactions. Houses the nested `Transaction` and `OrderedItem` inner classes. Declares the abstract method `getComputationFactor()` which must be implemented by all subclasses.

### Transaction *(nested inner class of Customer)*
Represents a single purchase activity under a customer account. Holds a list of ordered items and handles subtotal computation and final amount calculation by applying the customer's computation factor.

### OrderedItem *(nested inner class of Transaction)*
Represents a single item within a transaction. Stores the item name, quantity, and unit price, and computes the item-level subtotal.

### RegularCustomer
Extends `Customer`. Overrides `getComputationFactor()` to return `1.00`, meaning no discount is applied.

### VIPCustomer
Extends `Customer`. Overrides `getComputationFactor()` to return `0.85`, applying a 15% discount on the transaction subtotal.

## Predefined Values

| Item       | Unit Price (₱) |
|------------|---------------|
| Book       | 150.00        |
| Pen        | 20.00         |
| Notebook   | 50.00         |
| Calculator | 600.00        |
| Backpack   | 800.00        |

| Customer Type | Computation Factor |
|---------------|--------------------|
| Regular       | ×1.00 (0% discount) |
| VIP           | ×0.85 (15% discount) |

## How to Run

### Run It Online (No Setup Required)

[![Run on JDoodle](https://img.shields.io/badge/Run%20on-JDoodle-blue?style=for-the-badge&logo=java)](https://www.jdoodle.com/ga/vG1glE1maTfqItl7XS%2Fdsg%3D%3D)

### Local Setup

1. Ensure Java JDK is installed (Java 8 or higher)
2. Clone or download this repository
3. Compile all Java files:
```bash
javac *.java
```
4. Run the program:
```bash
java Main
```

## Sample Output

```
===== Retail Ordering System =====

Transactions of Customer John (Regular):

=== Transaction T1 ===
Items Ordered:
  - Book: 2 x 150.00 pesos = 300.00 pesos
  - Pen: 5 x 20.00 pesos = 100.00 pesos
Subtotal: 400.00 pesos
Computation Factor: 1.00
Final Amount: 400.00 pesos

=== Transaction T2 ===
Items Ordered:
  - Notebook: 3 x 50.00 pesos = 150.00 pesos
  - Calculator: 1 x 600.00 pesos = 600.00 pesos
Subtotal: 750.00 pesos
Computation Factor: 1.00
Final Amount: 750.00 pesos

Transactions of Customer Maria (VIP):

=== Transaction T1 ===
Items Ordered:
  - Book: 1 x 150.00 pesos = 150.00 pesos
  - Notebook: 4 x 50.00 pesos = 200.00 pesos
Subtotal: 350.00 pesos
Computation Factor: 0.85
Final Amount: 297.50 pesos

=== Transaction T2 ===
Items Ordered:
  - Calculator: 2 x 600.00 pesos = 1200.00 pesos
  - Backpack: 1 x 800.00 pesos = 800.00 pesos
Subtotal: 2000.00 pesos
Computation Factor: 0.85
Final Amount: 1700.00 pesos


Developed by: Jio Perey
```

## Sample Test Cases

| Label  | Customer | Transaction | Items Ordered        | Qty  | Unit Price  | Subtotal Computation    | Factor | Final   |
|--------|----------|-------------|----------------------|------|-------------|-------------------------|--------|---------|
| REG-T1 | John     | T1          | Book, Pen            | 2, 5 | 150, 20     | 300 + 100 = 400         | ×1.00  | 400.00  |
| REG-T2 | John     | T2          | Notebook, Calculator | 3, 1 | 50, 600     | 150 + 600 = 750         | ×1.00  | 750.00  |
| VIP-T1 | Maria    | T1          | Book, Notebook       | 1, 4 | 150, 50     | 150 + 200 = 350         | ×0.85  | 297.50  |
| VIP-T2 | Maria    | T2          | Calculator, Backpack | 2, 1 | 600, 800    | 1200 + 800 = 2000       | ×0.85  | 1700.00 |

## Key OOP Concepts Demonstrated

- **Abstraction**: `Customer` is an abstract class with the abstract method `getComputationFactor()`, forcing subclasses to define their own pricing logic
- **Inheritance**: `RegularCustomer` and `VIPCustomer` both extend `Customer`, inheriting its fields and methods
- **Composition**: `Transaction` is a nested inner class of `Customer`, and `OrderedItem` is a nested inner class of `Transaction` — neither can exist independently of its parent
- **Encapsulation**: All fields are private, accessed only through defined methods
- **Polymorphism**: `getComputationFactor()` is overridden in each subclass, allowing different behavior based on customer type

## Class Relationships

- **Customer & RegularCustomer** — Inheritance (extends)
- **Customer & VIPCustomer** — Inheritance (extends)
- **Customer & Transaction** — Composition (nested inner class, 1 to 0..*)
- **Transaction & OrderedItem** — Composition (nested inner class, 1 to 0..*)

## Technologies Used

- Java
- Object-Oriented Programming

## Author

- Jio Perey
- April 13, 2026

## License

This project is open source and available for educational purposes.
