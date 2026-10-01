# Database

Database design for the Bristol Regional Food Network digital marketplace.

## Contents

- [Core tables](#core-tables)
- [Ordering and payments](#ordering-and-payments)
- [Notifications](#notifications)
- [Lower priority: traceability and community](#lower-priority-traceability-and-community)

---

## Core tables

### User table
- ID
- First name - Mandatory
- Surname - Mandatory
- Phone number - Mandatory, Unique
- Email - Mandatory, Unique
- Password_hash - Mandatory
- Role - Mandatory (customer / producer / admin)
- Customer type (individual / community group / restaurant or café)
- Location ID (FK)
- Is active
- Created date - Mandatory
- Created by - Mandatory
- Updated date
- Updated by

### Location table
- ID
- House number/street
- Town
- County / City
- Region
- Postcode - Mandatory
- Latitude
- Longitude
- Created date - Mandatory
- Created by - Mandatory

### Producer table
- ID
- User ID (FK, Mandatory)
- Name - Mandatory
- Description
- Contact email - Mandatory, Unique
- Contact phone - Mandatory, Unique
- Location ID (FK)
- Organic certification status
- Payout account ID (from the payment provider, not bank details)
- Is active
- Created date - Mandatory
- Created by - Mandatory
- Updated date
- Updated by

### Category table
- ID
- Name - Mandatory, Unique
- Created date - Mandatory
- Created by - Mandatory

### Product table
- ID
- Producer ID (FK, Mandatory)
- Category ID (FK, Mandatory)
- Name - Mandatory
- Description
- Price - Mandatory
- Unit (kg, loaf, jar)
- Stock quantity
- Available from
- Available to
- Harvest date
- Best-before date
- Organic status
- Allergen warnings
- Batch code
- Is active
- Created date - Mandatory
- Created by - Mandatory
- Updated date
- Updated by

### Discount table
- ID
- Code
- Type (percentage / fixed)
- Amount - Mandatory
- Valid from
- Valid to
- Product ID (FK, optional, for surplus discounts)
- Created date - Mandatory
- Created by - Mandatory

---

## Ordering and payments

### Order table
- ID
- User ID (FK, Mandatory)
- Discount ID (FK, optional)
- Status
- Subtotal
- Discount amount
- Total amount
- Delivery or collection
- Delivery Location ID (FK)
- Requested fulfilment date
- Created date - Mandatory
- Created by - Mandatory
- Updated date
- Updated by

### Producer order table
One per producer in each order; gives each producer their own view and status.

- ID
- Order ID (FK, Mandatory)
- Producer ID (FK, Mandatory)
- Status
- Delivery or collection
- Fulfilment date (at least 48 hours after the order date)
- Subtotal
- Commission rate (5%)
- Commission amount
- Producer amount
- Distance in miles (food miles)
- Created date - Mandatory
- Created by - Mandatory
- Updated date
- Updated by

### Order line item table
- ID
- Order ID (FK, Mandatory)
- Producer order ID (FK, Mandatory)
- Product ID (FK, Mandatory)
- Quantity - Mandatory
- Unit price at purchase - Mandatory
- Line total
- Created date - Mandatory
- Created by - Mandatory

### Payment table
- ID
- Order ID (FK, Mandatory)
- User ID (FK, Mandatory)
- Provider (e.g. Stripe test mode)
- Provider transaction ID - Unique
- Amount
- Currency
- Status
- Refunded amount
- Created date - Mandatory
- Created by - Mandatory

### Receipt table
- ID
- Order ID (FK, Mandatory)
- Payment ID (FK, Mandatory)
- Receipt number - Unique
- Total paid
- Created date - Mandatory
- Created by - Mandatory

### Payout table
Weekly settlements to producers.

- ID
- Producer ID (FK, Mandatory)
- Period start
- Period end
- Gross amount
- Commission
- Net amount
- Status
- Paid date
- Provider payout reference
- Created date - Mandatory
- Created by - Mandatory

### Payout item table
Links each payout to the producer orders it covers, for the audit trail.

- ID
- Payout ID (FK)
- Producer order ID (FK)
- Amount
- Created date - Mandatory
- Created by - Mandatory

---

## Notifications

### Notification table
- ID
- User ID (FK)
- Producer order ID (FK, optional)
- Message
- Is read
- Created date - Mandatory
- Created by - Mandatory

---

## Lower priority: traceability and community

### Food safety notice table
- ID
- Producer ID (FK)
- Product ID (FK)
- Order ID (FK)
- Batch code
- Message
- Created date - Mandatory
- Created by - Mandatory

### Surplus listing table
- ID
- Product ID (FK)
- Discount price
- Quantity
- Expires at
- Created date - Mandatory
- Created by - Mandatory

### Post table
Recipes, storage guidance and farm stories.

- ID
- Producer ID (FK)
- Product ID (FK, optional)
- Type
- Title
- Body
- Published date
- Created date - Mandatory
- Created by - Mandatory
