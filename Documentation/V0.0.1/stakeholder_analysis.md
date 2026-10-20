# Bristol Regional Food Network - Digital Marketplace
## Stakeholder Analysis: External Customer Focus

### 1. Overview

The Bristol Regional Food Network Digital Marketplace connects customers with local food producers. Customers can explore products, buy from several producers in one marketplace order, pay through an external payment provider, and receive order and delivery or collection information.

This analysis focuses on external customers. It is aligned to the three major features in the Features Specification (v1.1): **Ordering (ORD)**, **Product Exploration (EXP)** and **Delivery (DEL)**.

### 2. Stakeholder Identification

#### 2.1 Primary Stakeholders: External Customers

| Customer Segment | Who They Are | Why They Use the Marketplace | Main Barrier Today | Interest | Influence |
|---|---|---|---|---|---|
| Individuals and families | Households with strong demand for locally sourced produce | Buy from several local producers in one purchase | Visiting multiple farm shops during limited opening hours | High | Medium |
| Community groups | Educational institutions, care facilities and voluntary organisations | Reliable, consistent local suppliers for catering | Difficulty identifying reliable sources | High | High (larger, repeat orders) |
| Independent restaurants and cafés | Small food businesses wanting to source locally | One checkout for many small suppliers | Administrative overhead of managing multiple supplier relationships | High | High (larger, repeat orders) |

#### 2.2 Secondary External Stakeholders

| Stakeholder | Role | Why They Matter to Customers |
|---|---|---|
| Food producers | List products, hold stock, receive notifications, fulfil their part of an order, and update fulfilment status | Listing accuracy and fulfilment determine whether customers receive what they ordered |
| External payment provider | Processes payments, reports outcomes, and supplies retry and status-checking mechanisms | Determines whether checkout succeeds and how failures and uncertain outcomes are handled |

#### 2.3 Internal Stakeholders

The project supervisor and the development team deliver and assess the system. They are accountable for meeting the customer needs below but are not analysed further here.

### 3. Customer Needs and Expectations

#### 3.1 Needs Common to All Customers

| Customer Need | What the Customer Expects | Feature Reference |
|---|---|---|
| Easy discovery | Browse products with names, descriptions, prices and producer details, and search by name with a clear message when nothing matches | EXP-01 to EXP-03, EXP-06 to EXP-08 |
| Category browsing | Filter by food type (vegetables, dairy, bakery goods, preserves, seasonal specialities) | EXP-09, EXP-10 |
| Trust in provenance | See producer details and farm or product origin | EXP-11, EXP-12 |
| Accurate availability | See which products are available, and be told when an item is unavailable or the quantity is insufficient, with the chance to amend the basket | EXP-04, EXP-05, ORD-07, ORD-09 |
| Fair time to pay | Stock reserved for 10 minutes at checkout, and rechecked if the reservation expires | ORD-08, ORD-10, ORD-23 |
| Flexible basket | One basket for several producers, with quantities that can be changed and a running subtotal | ORD-01 to ORD-06 |
| Transparent pricing | Itemised costs and total before paying, with delivery included in producer prices and no separate marketplace delivery charge | ORD-12 to ORD-15 |
| Clear fulfilment arrangements | Delivery or collection method and instructions shown separately for each producer, before and after ordering | ORD-11, DEL-01 to DEL-03, DEL-08 |
| Realistic timing | Fulfilment dates that respect the two-business-day preparation period | ORD-16, DEL-04 |
| Safe, recoverable payment | Clear outcomes for success, decline and failure, a retry where permitted, no duplicate charges or orders, and sensible handling of uncertain outcomes | ORD-17 to ORD-22 |
| Clear confirmation | Unique order reference, items, total, payment status and fulfilment details | ORD-27, ORD-28, DEL-05 to DEL-08 |
| Visibility after purchase | View the latest fulfilment status of the order | DEL-14 |

#### 3.2 Segment-Specific Needs

**Individuals and families**
- Simple browsing, basket and checkout that need no prior knowledge of the producers.
- One purchase across several producers in place of several shop visits.
- Fulfilment instructions that make it easy to plan around producers' limited opening hours.

**Community groups**
- Confidence that suppliers are reliable and consistent. This relies on accurate stock validation and fulfilment status updates.
- A retrievable order reference and confirmation summary for internal record-keeping.
- Predictable fulfilment dates, because catering is usually planned in advance.
- Detailed allergen and certification information, which is critical when catering for vulnerable groups (see section 7, as it is not in initial scope).

**Independent restaurants and cafés**
- Low administrative effort across several suppliers, through one basket, one payment and one order reference.
- Itemised, producer-by-producer order records for business accounting.
- Reliable stock checking and reservation, because larger quantities raise the impact of overselling.
- Dependable fulfilment so menus are not disrupted.

### 4. How Secondary Stakeholders Affect Customers

| Stakeholder | Effect on Customers | Requirement to Protect the Customer |
|---|---|---|
| Food producers | Accurate listings and stock, timely preparation, and honest fulfilment updates | Producer accounts and access limited to their own orders (DEL-09, DEL-10, DEL-13); notification after confirmation (ORD-32); at least two business days' preparation time |
| External payment provider | Checkout success or failure, and the safety of payment details | The marketplace integrates with the provider's interface (ORD-17) and follows its retry and status-checking mechanisms (ORD-20, ORD-21); payment handling is kept separate from order confirmation so an order is confirmed only after successful payment (ORD-28); testing uses the provider's sandbox or test environment |

### 5. Customer Engagement Plan

| Stakeholder | Engagement Method | Timing |
|---|---|---|
| Individuals and families | Usability testing of search, basket, checkout and confirmation | Requirements gathering and testing |
| Community groups | Requirements discussions on reliability, fulfilment information and order records | Requirements gathering and review of order workflows |
| Independent restaurants and cafés | Requirements discussions on multi-producer ordering and itemised order breakdowns | Requirements gathering and review of order workflows |
| Food producers | Feedback on notifications, order views and fulfilment updates | Requirements gathering and relevant reviews |
| External payment provider | Technical documentation and sandbox or test environment agreed with the provider | Implementation and testing |

Where direct access to real customers is limited, personas based on the three customer segments can be used during design and testing.

### 6. Key Customer-Related Risks

| Risk | Most Affected | Mitigation |
|---|---|---|
| Overselling through stock inaccuracy or concurrent purchases | All, especially restaurants and community groups ordering larger quantities | Recheck stock at checkout, reserve it for 10 minutes and revalidate on expiry (ORD-07, ORD-08, ORD-10) |
| Reservation expires while the customer is paying | All | Coordinate payment attempts with the reservation so no unfulfillable order is confirmed (ORD-23) |
| Payment failure or uncertain outcome | All | Clear messages, retries where permitted, and status checking before any retry (ORD-19 to ORD-21) |
| Duplicate charges or orders from retries and callbacks | All | Duplicate-processing prevention (ORD-22) |
| Unclear fulfilment responsibility in multi-producer orders | All | Producer-specific order elements and fulfilment information (ORD-25, DEL-03) |
| Confusion over pricing and total | All | Itemised review and a single total using delivery-inclusive prices (ORD-13 to ORD-15) |
| Insufficient preparation time | All | Apply the two-business-day rule wherever fulfilment dates are selected (ORD-16, DEL-04) |
| Producers not updating fulfilment status | Community groups, restaurants and cafés | Simple producer tools and restricted, clear update controls (DEL-12, DEL-13) |
| Poor search or navigation | Individuals and families | Clear categories, effective search, and usability testing |
| Missing allergen and certification information | Community groups, families | Not in initial scope, so decide whether to bring forward (see section 7) |

### 7. Customer Needs Outside the Initial Release

The case study describes customer needs that are not in the current Features Specification. They are recorded so they are not lost.

- Harvest dates and seasonal availability indicators
- Organic certification status, allergen warnings and best-before dates
- Food miles calculations
- Surplus produce communication with last-minute discounts
- Producer recipes, storage guidance and farm stories

Allergen information is the most significant gap for community groups and families. The team should confirm whether it is deferred deliberately or should be brought into the initial release.
