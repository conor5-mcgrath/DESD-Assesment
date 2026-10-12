# Bristol Regional Food Network - Digital Marketplace
## Initial Product Backlog

### 1. Purpose

This document establishes the initial product backlog for the Bristol Regional Food Network Digital Marketplace.

The backlog translates the stakeholder requirements into user stories and acceptance criteria that can guide development, testing, and prioritisation.

The project is organised into four core modules:

1. Product exploration and searching
2. Basket management
3. Order confirmation
4. Delivery confirmation

The backlog is an initial proposal and should be refined as the project progresses and feedback is received from the project supervisor and team.

### 2. Prioritisation Method

The MoSCoW method will be used to prioritise backlog items.

- **Must have:** Essential functionality required for the core marketplace workflow.
- **Should have:** Important functionality that can be delivered after the essential features.
- **Could have:** Desirable improvements if time and resources permit.
- **Won't have in the initial release:** Functionality deliberately deferred from the current project scope.

### 3. Initial Product Backlog

| ID | Module | User Story | Priority | Acceptance Criteria |
|---|---|---|---|---|
| PB01 | Product Exploration | As a customer, I want to browse available products so that I can discover local food. | Must have | Products display their names, descriptions, prices, and producer information. |
| PB02 | Product Exploration | As a customer, I want to search for products by name so that I can find specific items quickly. | Must have | Matching products are displayed, and a suitable message appears when no products match the search. |
| PB03 | Product Exploration | As a customer, I want to browse products by category so that I can find relevant items easily. | Should have | Customers can filter products by categories such as vegetables, dairy, bakery goods, preserves, and seasonal specialities. |
| PB04 | Product Exploration | As a customer, I want to see product availability so that I do not select unavailable items. | Must have | Product listings display current availability or clearly identify unavailable products. |
| PB05 | Product Exploration | As a customer, I want to view product origin and producer information so that I know where my food comes from. | Should have | Product details identify the producer and display available farm origin information. |
| PB06 | Basket | As a customer, I want to add products to my basket so that I can collect items before checkout. | Must have | Selected products appear in the basket with their names, quantities, prices, and producer associations. |
| PB07 | Basket | As a customer, I want to change quantities or remove products so that I can manage my order. | Must have | Quantity changes update the basket, and removed products no longer contribute to the total. |
| PB08 | Basket | As a customer, I want to see my basket subtotal so that I understand the cost of my selected products. | Must have | The system calculates the subtotal from product prices and selected quantities. |
| PB09 | Basket | As a customer, I want to order products from multiple producers in one basket so that I can shop conveniently. | Must have | Products from different producers can be held in the same basket, and every item retains its producer association. |
| PB10 | Basket | As a customer, I want the system to validate stock at checkout so that I do not pay for unavailable quantities. | Must have | The system checks current stock for every basket item and asks the customer to amend the basket if stock is insufficient. |
| PB11 | Basket | As a customer, I want to review delivery or collection arrangements for each producer so that I understand how I will receive my items. | Must have | The checkout review identifies each relevant producer and displays applicable fulfilment arrangements where available. |
| PB12 | Order Confirmation | As a customer, I want to review my order before confirming it so that I can verify the items and costs. | Must have | The review displays products, quantities, prices, producer information, applicable charges, and the total payable. |
| PB13 | Order Confirmation | As a customer, I want to pay through a simulated payment service so that I can complete a purchase safely in testing. | Must have | Payment processing uses a sandbox or mock gateway and does not require real payment details. |
| PB14 | Order Confirmation | As a customer, I want confirmation after successful payment so that I know my order has been accepted. | Must have | A successful payment results in a confirmed order and a unique order reference. |
| PB15 | Order Confirmation | As a customer, I want to know when payment is declined so that I can correct the problem or retry. | Must have | The system displays an appropriate message, leaves the order unconfirmed, and allows a safe retry. |
| PB16 | Order Confirmation | As a customer, I want temporary payment-service failures to be handled appropriately so that I can retry without losing my order. | Must have | The system follows a defined retry or recovery path and prevents duplicate confirmed orders or payment attempts that could cause duplicate charges. |
| PB17 | Order Confirmation | As a producer, I want my part of a multi-producer order to be identified separately so that I can prepare the correct items. | Must have | One overall marketplace order contains separate producer-specific order elements with the correct products and quantities. |
| PB18 | Order Confirmation | As a marketplace administrator, I want the system to calculate a 5% commission so that the network's share is recorded accurately. | Must have | The system calculates and records 5% of the agreed commissionable order amount. |
| PB19 | Order Confirmation | As a producer, I want to receive notification of my confirmed orders so that I can prepare them for fulfilment. | Must have | Each relevant producer is notified after successful payment and confirmation, with their own products and quantities. |
| PB20 | Delivery Confirmation | As a customer, I want to see delivery or collection arrangements for each producer so that I know how to receive my order. | Must have | The confirmation identifies each producer's applicable delivery or collection method and available instructions. |
| PB21 | Delivery Confirmation | As a customer, I want an order confirmation summary so that I can refer to my purchase details. | Must have | The summary contains an order reference, products, quantities, total payable, payment status, and relevant fulfilment information. |
| PB22 | Delivery Confirmation | As a producer, I want to view my confirmed order details so that I can fulfil orders correctly. | Should have | Producer-facing order details display the relevant products, quantities, and available fulfilment instructions. |
| PB23 | Delivery Confirmation | As a customer, I want to know when my order is ready for collection or has been dispatched so that I can plan to receive it. | Should have | Where fulfilment status updates are included, the system displays the latest recorded status. |
| PB24 | Order Confirmation | As a marketplace administrator, I want transaction and commission records so that financial activity can be audited. | Should have | The system records order references, payment outcomes, order totals, producer allocations, and commission amounts. |

### 4. Business Rules

#### 4.1 Multi-Producer Orders

The system must create one overall marketplace order for the customer and associate it with separate producer-specific order elements.

Every order item must retain its producer association, quantity, and purchase price.

#### 4.2 Stock Validation

The system must validate stock when the customer proceeds to checkout.

If a product is unavailable or the requested quantity exceeds available stock:

- The customer must be informed.
- The affected product must be identified.
- The customer must be allowed to amend the basket.
- The system must not proceed with an invalid order.

Inventory quantities must be updated only after successful payment and order confirmation. The implementation should also account for concurrent purchases to reduce the risk of overselling.

#### 4.3 Payment Processing

All payment functionality must use a sandbox or simulated payment gateway.

The system must support:

- Successful payments.
- Declined payments.
- Temporary payment-service failures.
- Safe payment retries.
- Prevention of duplicate order confirmation.
- Appropriate handling of uncertain payment outcomes.

A temporary technical failure must not automatically be treated as a declined payment. If the outcome is uncertain, the system should check the transaction status or follow a recovery process before retrying.

#### 4.4 Marketplace Commission

The marketplace commission is 5% of the agreed commissionable order amount.

For example, if the commissionable product total is £40:

- Commission = £40 x 0.05 = £2.
- Producer allocation before other agreed adjustments = £40 - £2 = £38.

For multi-producer orders, the system must calculate the amount attributable to each producer and record the relevant commission.

The team must agree whether delivery charges, discounts, and other adjustments are included in the commissionable amount before implementation.

#### 4.5 Delivery and Collection

Delivery and collection arrangements must be identified for each producer. The system must not assume that different producers share one fulfilment arrangement.

The background requirements specify a minimum preparation lead time of 48 hours. The team should clarify how this requirement affects checkout and customer-selected fulfilment dates and implement appropriate validation where scheduling is included in scope.

### 5. Definition of Done

A backlog item can be considered complete when:

- Its acceptance criteria have been met.
- The relevant functionality has been tested.
- Appropriate validation and error handling are implemented.
- The code has been reviewed by another team member where practical.
- The functionality integrates with the relevant modules.
- Necessary documentation has been updated.
- Payment-related functionality has been tested exclusively using a sandbox or simulated service.

