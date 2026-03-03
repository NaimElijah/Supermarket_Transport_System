# SuperLee – Supermarket Management System

A Java-based **CLI management system** for a supermarket environment, combining:

- **Employee / HR management**
- **Shift and availability management**
- **Transport and logistics management**
- **Role-based permissions and access control**
- **SQLite-based persistence**

This project was built with a layered architecture and provides a full command-line workflow for managing employees, shifts, trucks, sites, and transports in one system.

## Note
#### The full System Guide is in the /docs folder, in instructions.md.

---

## Overview

**SuperLee** is a supermarket operations system designed to support two major business areas:

### 1. Employee Management Module
Handles workforce-related operations such as:

- Employee creation and management
- Role and permission assignment
- Shift creation and editing
- Assignment board
- Availability board
- Branch association

### 2. Transport Management Module
Handles transportation and logistics such as:

- Shipping areas and sites
- Truck fleet management
- Driver and truck assignment
- Transport creation and tracking
- Delivery item handling
- Route and logistics-related workflows

The system is operated through a **command-line interface (CLI)** and uses **SQLite** for persistent data storage.

---

## Features

### Employee / HR
- Create, update, deactivate, and view employees
- Manage roles and permissions
- Assign and remove roles from employees
- Create and manage shifts
- Assign employees to shifts
- Track employee availability
- View employee schedules

### Transport / Logistics
- Manage trucks, sites, and shipping areas
- Create and update transports
- Assign drivers and vehicles
- Track transport status
- Manage transported items and delivery flow

### System / Technical
- Role-based authorization
- Layered architecture:
  - Presentation Layer
  - Service Layer
  - Domain Layer
  - Data Access Layer
- SQLite database integration
- JSON support with Jackson
- Maven-based build
- Fat JAR packaging for simple execution

---

## Tech Stack

- **Java 23**
- **Maven**
- **SQLite**
- **Jackson**
- **JUnit 5**
- **SLF4J**

---

## Project Structure

```text
Supermarket_Transport_System-main/
├── dev/                          # Source code
│   ├── DataAccessLayer/
│   ├── DomainLayer/
│   ├── DTOs/
│   ├── PresentationLayer/
│   ├── ServiceLayer/
│   ├── Util/
│   └── Main.java
├── docs/                         # Project docs and usage instructions
├── data/                         # JSON seed/config-related data
├── lib/                          # External jars / local dependencies
├── release/                      # Prebuilt JARs and DB files
├── pom.xml
└── README.md
```
> Note: the project uses a custom Maven source directory: `dev/` instead of the usual `src/main/java`.

---

## Architecture

The system follows a **layered design**:

* **Presentation Layer**
  CLI menus and user interaction

* **Service Layer**
  Application use-cases and orchestration

* **Domain Layer**
  Business logic and core entities

* **Data Access Layer**
  SQLite persistence and repository/DAO logic

This separation makes the project easier to maintain, test, and extend.

---

## Getting Started

### Prerequisites

Make sure you have:

* **Java 23**
* **Maven 3.9+**

Check versions:

```bash
java -version
mvn -version
```

---

## How to Run

There are two simple ways to run the project.

### Option 1 — Run the prebuilt JAR

From the project root:

```bash
java -jar release/adss2025_v02.jar
```

This is the fastest way to start the system.

---

### Option 2 — Build from source with Maven

#### 1. Package the application

```bash
mvn clean package
```

#### 2. Run the generated fat JAR

```bash
java -jar target/superLee-1.0.0-jar-with-dependencies.jar
```

> Depending on your Maven configuration or future version changes, the file name in `target/` may vary slightly.

---

## What Happens on Startup

When the application starts, it asks whether to use **minimal data**.

* **Minimal mode** → lightweight setup for development/testing
* **Full mode** → broader preloaded dataset for the full system experience

The system then initializes the SQLite database and launches the main CLI.

---

## Default Access / Demo User

The system includes a preloaded admin user:

* **Admin ID:** `123456789`

This user has full permissions and is useful for exploring the system without manually creating roles first.

---

## Main Modules

After login, the main menu allows access to:

```text
1. Employee Module
2. Transport Module
3. Exit
```

### Employee Module

Includes:

* Employees
* Roles
* Permissions
* Shifts
* Assignment Board
* Availability Board

### Transport Module

Includes:

* Trucks
* Sites
* Shipping Areas
* Transports
* Driver-related transport operations

---

## Database

The project uses **SQLite**.

Relevant database files include:

* `superLee.db`
* `SuperLee_Minimal.db`
* `release/superLee.db`
* `release/SuperLee_Minimal.db`

The application initializes required tables programmatically and supports both **full** and **minimal** data setups.

---

## Documentation

Detailed usage and system instructions are available in:

* `docs/instructions.md`
* `docs/Documentation.pdf`
* `docs/System Permissions Analysis.md`

These documents explain:

* user flows
* permissions
* available operations
* initialization behavior
* module-specific instructions

---

## Dependencies

The project uses the following dependencies:

- **Jackson** (version 2.16.0) - For JSON processing
- **SQLite JDBC** (version 3.45.1.0) - For database connectivity
- **JUnit Jupiter 5** (version 5.8.1) - For testing
- **Maven Exec Plugin** (version 3.0.0) - For running the application

---

## Notes for Developers

* Source code lives under `dev/`
* Main entry point:

```java
Main.java
```

* The CLI starts from:

```java
PresentationLayer.MainCLI
```

* The project uses a factory-style initialization flow via:

```java
DomainLayer.SystemFactory
```

---

## Possible Improvements

Future enhancements could include:

* Standardizing the project layout to `src/main/java`
* Adding automated unit and integration tests
* Adding Docker support
* Improving configuration management
* Adding a GUI or web interface
* Expanding reporting and analytics

---

## Team Members
* Sub-Team A (Transport Module)
   * Naim Elijah
* Sub-Team B (HR Module)
   * Rotem Guetta
   * Gabriel Rozental

---

## License

This project was created for educational / portfolio purposes.

---

## Quick Run Summary

```bash
# Run prebuilt version
java -jar release/adss2025_v02.jar

# Or build from source
mvn clean package
java -jar target/superLee-1.0.0-jar-with-dependencies.jar
```

Admin login for testing:

```text
123456789
```
