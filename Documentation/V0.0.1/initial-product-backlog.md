# Bristol Regional Food Network - Digital Marketplace
## Initial Product Backlog

### 1. Purpose

This document establishes the initial product backlog for the Bristol Regional Food Network Digital Marketplace. It translates the Features Specification (v1.1) into user stories and acceptance criteria that guide development, testing and prioritisation.

The backlog is organised around the three major features: **Ordering**, **Product Exploration** and **Delivery**. Each item references the feature IDs it implements (ORD, EXP and DEL), so coverage can be checked against the specification. The backlog is an initial proposal and should be refined as feedback is received.

### 2. Initial Product Backlog

#### 2.1 Product Exploration

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB01 | As a customer, I want to browse products so that I can discover local food. | Must | Listings show product names, descriptions, prices and the producer. | EXP-01, 02, 03 |
| PB02 | As a customer, I want to search for products by name so that I can find specific items quickly. | Must | Matching products are displayed, and a suitable message appears when none match. | EXP-06, 07, 08 |
| PB03 | As a customer, I want to see product availability so that I avoid selecting unavailable items. | Must | Listings show whether each product is available, and unavailable products are clearly distinguished. | EXP-04, 05 |
| PB04 | As a customer, I want to browse and filter by category so that I can find relevant items easily. | Should | Customers can browse configured categories and filter by food type (vegetables, dairy, bakery goods, preserves, seasonal specialities). | EXP-09, 10 |
| PB05 | As a customer, I want to view producer details and product origin so that I know where my food comes from. | Should | Customers can access producer information and available farm or product-origin information. | EXP-11, 12 |

#### 2.2 Ordering: Basket and Stock

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB06 | As a customer, I want to add products to a basket and view it so that I can collect items before checkout. | Must | Available products can be added, and the basket shows products, quantities, prices and producers. | ORD-01, 02 |
| PB07 | As a customer, I want to change quantities or remove products so that I can manage my order. | Must | Quantity changes update the basket, and removed products no longer contribute to the total. | ORD-03, 04 |
| PB08 | As a customer, I want to see my basket subtotal so that I understand the cost. | Must | The subtotal is calculated from product prices and selected quantities. | ORD-05 |
| PB09 | As a customer, I want to order from several producers in one basket so that I can shop conveniently. | Must | Products from different producers can share a basket, and each item keeps its producer association. | ORD-06 |
| PB10 | As a customer, I want stock rechecked at checkout so that I do not pay for unavailable quantities. | Must | Every item is rechecked when the customer proceeds to ordering. Affected products are identified, the customer is informed and can amend the basket, and an invalid order does not proceed. | ORD-07, 09 |
| PB11 | As a customer, I want my stock reserved while I check out so that items do not sell out during payment. | Must | After successful validation, requested quantities are reserved for 10 minutes. | ORD-08 |
| PB12 | As a customer, I want an expired reservation handled so that I am not charged for unavailable stock. | Must | If a reservation expires before the order is completed, stock is revalidated before proceeding. | ORD-10 |
| PB13 | As a customer, I want to review delivery or collection arrangements for each producer so that I know how I will receive my items. | Must | Checkout shows each relevant producer's arrangements. | ORD-11, DEL-01, 03 |

#### 2.3 Ordering: Checkout and Order Review

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB14 | As a customer, I want to review my order before paying so that I can verify items and costs. | Must | The review shows products, quantities, unit prices and producer associations. | ORD-12, 13 |
| PB15 | As a customer, I want a clear total so that I know what I will pay. | Must | The total uses producer-listed prices, which include any producer delivery costs. No separate marketplace delivery charge is added. | ORD-14, 15 |
| PB16 | As a customer, I want fulfilment dates to respect preparation time so that producers can prepare my order. | Should | Where fulfilment dates are selected, the two-business-day preparation rule is applied. | ORD-16, DEL-04 |

#### 2.4 Ordering: External Payment Integration

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB17 | As a customer, I want to pay through an external payment provider so that my payment is processed securely. | Must | Payment requests are sent to the provider through its supported integration interface. | ORD-17 |
| PB18 | As a customer, I want to be told when payment is declined or fails so that I can correct the problem. | Must | The outcome is communicated and the order stays unconfirmed unless payment succeeds. | ORD-19 |
| PB19 | As a customer, I want to retry payment when permitted so that I do not lose my order. | Must | The customer can retry when the provider permits it, following the provider's retry process. | ORD-20 |
| PB20 | As a customer, I want uncertain payment outcomes handled so that I am not wrongly charged or refused. | Must | The system uses the provider's status-checking or recovery mechanism before treating an uncertain outcome as a failure. | ORD-21 |
| PB21 | As a customer, I want protection from duplicate charges so that I am only charged once. | Must | Repeated requests, callbacks or retries never create duplicate confirmed orders or charges. | ORD-22 |
| PB22 | As a customer, I want payment and reservation coordinated so that I never receive a confirmation for an order that cannot be fulfilled. | Must | Payment attempts are handled alongside the 10-minute reservation, and no order is confirmed that cannot be fulfilled. | ORD-23 |

#### 2.5 Ordering: Order Creation, Commission and Audit

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB23 | As a customer, I want one marketplace order split by producer so that responsibility for each item is clear. | Must | One overall order contains a separate element per producer, and each item retains its producer, quantity and purchase price. | ORD-24, 25, 26 |
| PB24 | As a customer, I want confirmation after successful payment so that I know my order is accepted. | Must | A confirmed order with a unique reference is created only after successful payment and required validations. | ORD-18, 27, 28 |
| PB25 | As a customer, I want inventory updated on confirmation so that stock stays accurate for others. | Must | Stock is committed or deducted on confirmation, in line with the reservation mechanism. | ORD-29 |
| PB26 | As a marketplace administrator, I want a 5% commission calculated and allocated so that the network's share is recorded accurately. | Must | 5% of the commissionable product amount is calculated, and the amount attributable to each producer and the commission are recorded. | ORD-30, 31 |
| PB27 | As a producer, I want to be notified of confirmed orders so that I can prepare them. | Must | Each relevant producer is notified after confirmation, with only their own items and quantities. | ORD-32 |
| PB28 | As a marketplace administrator, I want transactions recorded so that financial activity can be audited. | Must | Order references, payment outcomes, order totals, producer allocations and commission amounts are recorded. | ORD-33 |
| PB29 | As a marketplace administrator, I want audit records retained and protected so that they are reliable. | Should | Records are retained indefinitely and cannot be edited or deleted through normal application functionality. | ORD-34, 35 |

#### 2.6 Delivery

| ID | User Story | Priority | Acceptance Criteria | Feature Ref |
|---|---|---|---|---|
| PB30 | As a customer, I want to see the delivery or collection method and instructions for each producer so that I know how to receive my order. | Must | The correct method and available instructions are shown for each producer in the order. | DEL-01, 02, 03 |
| PB31 | As a customer, I want an order confirmation summary so that I can refer to my purchase. | Must | The summary shows the order reference, items and quantities, total payable, payment status and fulfilment details. | DEL-05, 06, 07, 08 |
| PB32 | As a producer, I want to sign in to my account so that I can access producer functions. | Must | Producers authenticate through their accounts. | DEL-09 |
| PB33 | As a producer, I want to view my own confirmed orders so that I can fulfil them correctly. | Must | Producers see only the products and quantities they must fulfil, restricted to their own order information. | DEL-10, 11 |
| PB34 | As a producer, I want to record successful delivery or collection so that customers know the order is complete. | Should | Only the relevant authorised producer can update fulfilment status for their own order items. | DEL-12, 13 |
| PB35 | As a customer, I want to see my order's fulfilment status so that I can plan to receive it. | Should | The latest recorded fulfilment status is displayed. | DEL-14 |

### 3. Deferred Items (Won't Have in the Initial Release)

These are in the case study but not in the Features Specification, so they are deferred unless the team decides otherwise.

- Harvest dates and seasonal availability indicators
- Organic certification, allergen warnings and best-before dates
- Food miles calculation
- Surplus produce communication and last-minute discounts
- Recipes, storage guidance and farm stories
- Weekly producer payment settlements and tax-oriented reporting
- A separate marketplace delivery charge

### 4. Business Rules

#### 4.1 Multi-Producer Orders
- One overall marketplace order is created per purchase, with separate producer-specific order elements.
- Every order item retains its producer association, quantity and purchase price.

#### 4.2 Stock Validation and Reservation
- Stock is rechecked when the customer proceeds from the basket to the ordering stage.
- If a product is unavailable or the quantity is insufficient, the customer is informed, the affected product is identified, the customer can amend the basket, and the order does not proceed.
- After successful validation, stock is reserved for 10 minutes. If the reservation expires before completion, stock is revalidated.
- Inventory is committed or deducted only after successful payment and order confirmation. Concurrent purchases must be handled to reduce overselling.

#### 4.3 Payment Processing
- Payments are processed by an external payment provider, and the marketplace integrates with it and coordinates its responses with the order workflow.
- The system must handle successful, declined and failed payments, provider-supported retries, pending or uncertain outcomes, and duplicate prevention.
- A temporary technical failure must not be treated automatically as a declined payment. The system checks the transaction status or follows the provider's recovery process first.
- An order is confirmed only after successful payment and required validations.
- Testing uses the provider's sandbox or test environment, to be agreed with the provider. No real payment data is used in testing.

#### 4.4 Pricing and Marketplace Commission
- Delivery charges are included in producer-listed prices. The marketplace adds no separate delivery charge.
- Commission is 5% of the agreed commissionable product amount.
- Example: if the commissionable product total is £40, commission is £40 × 0.05 = £2, and the producer allocation before other agreed adjustments is £38.
- For multi-producer orders, the amount attributable to each producer and the relevant commission are calculated and recorded.
- The team must agree whether discounts and other adjustments are commissionable before implementation.

#### 4.5 Delivery, Collection and Preparation Time
- Fulfilment arrangements are identified per producer, and the system must not assume that producers share one arrangement.
- The minimum preparation period runs from the end of the business day on which the order is placed to the end of the second subsequent business day. For example, an order placed on Wednesday is due no earlier than Friday, subject to the business-day calendar.
- This rule is applied wherever fulfilment dates are selected.

#### 4.6 Audit Records
- Audit records are immutable through normal application functionality and retained indefinitely in the initial release.

### 5. Definition of Done

A backlog item is complete when:

- Its acceptance criteria are met.
- The functionality has been tested.
- Appropriate validation and error handling are implemented.
- The code has been reviewed by another team member where practical.
- It integrates with the relevant features.
- Documentation is updated.
- Payment-related functionality has been tested only in the provider's sandbox or test environment.
