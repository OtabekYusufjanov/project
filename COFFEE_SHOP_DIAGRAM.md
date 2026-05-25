# Smart Coffee Shop Management System - Project Diagram

## System Architecture Diagram

```mermaid
graph TB
    subgraph "Users"
        Customer["👤 Customer"]
        Staff["👥 Staff/Employee"]
        Manager["👨‍💼 Manager"]
    end
    
    subgraph "Frontend Layer"
        UI["User Interface"]
        Dashboard["Dashboard"]
        OrderPage["Order Management"]
        PaymentPage["Payment Processing"]
        InventoryPage["Inventory Page"]
        ReportPage["Reports Page"]
    end
    
    subgraph "Backend Layer"
        OrderService["Order Service"]
        PaymentService["Payment Service"]
        InventoryService["Inventory Service"]
        StaffService["Staff Management"]
        ReportService["Report Generator"]
    end
    
    subgraph "Data Layer"
        Database["MySQL Database"]
        Cache["Cache System"]
    end
    
    Customer --> UI
    Staff --> UI
    Manager --> Dashboard
    
    UI --> OrderPage
    UI --> PaymentPage
    UI --> InventoryPage
    UI --> ReportPage
    
    OrderPage --> OrderService
    PaymentPage --> PaymentService
    InventoryPage --> InventoryService
    Dashboard --> ReportService
    
    OrderService --> Database
    PaymentService --> Database
    InventoryService --> Database
    StaffService --> Database
    ReportService --> Database
    
    Database --> Cache
```

## Data Flow Diagram

```mermaid
graph LR
    Order["📋 Customer Order"]
    Process["⚙️ Process Order"]
    Payment["💳 Payment Processing"]
    Inventory["📦 Update Inventory"]
    Report["📊 Generate Report"]
    
    Order --> Process
    Process --> Payment
    Payment --> Inventory
    Inventory --> Report
```

## Process Flow Diagram

```mermaid
graph TD
    A["Start: Customer Places Order"]
    B["Order Received by System"]
    C{"Payment Successful?"}
    D["Update Inventory"]
    E["Notify Staff"]
    F["Generate Order Receipt"]
    G["Update Sales Report"]
    H["End: Order Complete"]
    
    A --> B
    B --> C
    C -->|Yes| D
    C -->|No| A
    D --> E
    E --> F
    F --> G
    G --> H
```

## Component Relationship Diagram

```mermaid
graph TB
    subgraph "Customer Facing"
        Menu["Menu System"]
        Cart["Shopping Cart"]
    end
    
    subgraph "Transaction"
        Order["Order Processing"]
        Payment["Payment Gateway"]
    end
    
    subgraph "Operations"
        Inventory["Inventory Tracker"]
        Staff["Staff Management"]
    end
    
    subgraph "Analytics"
        Reports["Sales Reports"]
        Analytics["Performance Analytics"]
    end
    
    Menu --> Cart
    Cart --> Order
    Order --> Payment
    Payment --> Inventory
    Inventory --> Staff
    Order --> Reports
    Reports --> Analytics
```

## Technology Stack

```mermaid
graph TB
    subgraph "Frontend"
        HTML["HTML"]
        CSS["CSS"]
        JS["JavaScript"]
    end
    
    subgraph "Backend"
        Python["Python"]
    end
    
    subgraph "Database"
        MySQL["MySQL"]
    end
    
    HTML --> JS
    CSS --> JS
    JS --> Python
    Python --> MySQL
```

## User Roles & Permissions

```mermaid
graph TB
    Manager["👨‍💼 Manager"]
    Staff["👥 Staff"]
    Customer["👤 Customer"]
    
    Manager --> |Full Access| AllFeatures["All Features"]
    Staff --> |Limited Access| OrderStaff["Orders & Inventory"]
    Customer --> |Public Access| Menu["Menu & Ordering"]
    
    AllFeatures --> |Dashboard<br/>Reports<br/>Settings|Reports["Analytics & Reports"]
    OrderStaff --> |Process Orders<br/>Update Stock|Inventory["Inventory Management"]
    Menu --> |Browse<br/>Order<br/>Checkout|Checkout["Payment"]
```
