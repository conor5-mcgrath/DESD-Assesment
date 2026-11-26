# Legal, Social, Ethical and Professional Considerations

**Project:** Bristol Regional Food Network (BRFN) Digital Marketplace
**Scope:** Use Case 2 – Customer Multi-Vendor Order, Checkout and Payment

> *BRFN and all associated entities are fictitious and used for educational purposes. All payment functionality is built and tested using a sandbox or simulated payment service with synthetic data only. This section is an analysis for project purposes, not legal advice.*

---

## 1. Introduction

The marketplace's checkout and payment functionality handles personal data, payments, stock commitments and the division of money between several producers and the network. This section sets out the legal, social, ethical and professional issues that apply to it and how the team's design responds to them.

| Stage | Consideration |
|---|---|
| Stock check at checkout | Accuracy of availability, honest messaging, avoiding overselling |
| Identify producers; delivery/collection arrangements | Consumer information duties, clear supplier responsibility, data shared with producers |
| Customer review and confirmation | Price transparency, contract formation |
| Create marketplace order and split into producer elements | Data minimisation, traceability, record keeping |
| Payment submission, success, decline, retry, service outage | Payment security, data protection, fair and safe failure handling |
| Inventory update and producer notification | Accurate stock, 48-hour producer notice |
| Per-producer amounts and 5% commission | Accurate calculation, audit trail, transparency |

---

## 2. Legal Considerations

### 2.1 Data protection (UK GDPR and Data Protection Act 2018)

Checkout processes customer names, contact and delivery details, order history and payment status.

- **Lawful basis:** Processing the order is necessary to perform the contract with the customer. Marketing consent must not be bundled into checkout.
- **Data minimisation across producers:** When an order is split into producer-specific elements, each producer should only receive the data needed to fulfil their part (customer name, delivery address or collection details, and their own items), not the full basket or other producers' items.
- **Controller roles:** BRFN and each producer are likely to act as controllers of the order data they handle. This should be defined in producer terms and the privacy notice.
- **Privacy notice:** Shown before payment, explaining that details are shared with the relevant producers and the payment provider.
- **Security:** Encryption in transit and at rest, role-based access, and audit logging. A personal data breach affecting individuals must be reported to the ICO within 72 hours.
- **Retention and rights:** Defined retention periods for order and payment records, and support for access, correction and erasure requests where no legal retention duty applies.
- **DPIA:** A Data Protection Impact Assessment is appropriate, as checkout combines payment, multi-party sharing and customer groups such as care facilities.

### 2.2 Payment processing and card security

- **PCI DSS:** The platform must not store or handle raw card numbers. Hosted payment fields and tokens from the sandbox provider keep the platform out of scope for most card data requirements. Only tokens, payment references and statuses are stored.
- **Regulated payment activity:** Collecting one payment and distributing it between producers and BRFN may fall under the Payment Services Regulations 2017. The design assumes a regulated payment provider with split-payment (marketplace) functionality carries out the transfer, rather than BRFN holding customer funds. This assumption should be confirmed with the company's legal team before live operation.
- **Strong Customer Authentication:** The flow must handle 3-D Secure steps, including failed or abandoned authentication, as a decline path.
- **Sandbox rule:** Only test environments, test card numbers and synthetic customers are used. No live payment systems or real financial data are used at any stage.

### 2.3 Consumer protection

- **Pre-contract information:** Under the Consumer Contracts Regulations 2013, the customer must be shown the total price including delivery charges, the seller(s), and delivery or collection arrangements before confirming. For multi-vendor orders this means showing each producer's items, charges and arrangements separately.
- **Cancellation:** The 14-day cancellation right does not apply to goods that deteriorate quickly, which covers most fresh produce. This exception must be clearly stated, and handled separately for longer-life items such as preserves.
- **Order acknowledgement and error correction:** The Electronic Commerce Regulations 2002 require the customer to be able to review and correct their order before submitting, and to receive an acknowledgement.
- **Unfair practices (Digital Markets, Competition and Consumers Act 2024):** No hidden charges at the final step, and no misleading stock or urgency indicators.
- **Contract formation:** Terms must state when the contract is formed (on successful payment and order confirmation) and that each producer is the seller of their own items.
- **Product descriptions:** Under the Consumer Rights Act 2015, goods must match their description. Harvest dates, farm origin and product details shown at checkout must reflect producer-supplied information.

### 2.4 Food information and traceability

- **Allergens and best-before dates:** Allergen information is legally required before purchase (Food Information Regulations 2014). The order summary should preserve allergen and best-before information for each item.
- **Traceability:** The order data linking customer, product and producer must be retained so that producers and BRFN can quickly contact affected customers if a food safety issue arises (General Food Law, Regulation 178/2002 as retained in UK law).

### 2.5 Financial records, commission and tax

- **Commission calculation:** The 5% commission and each producer's share must be calculated and stored for every order, using fixed-precision decimal or integer-pence arithmetic with a documented rounding rule, so that producer amounts plus commission always equal the amount charged.
- **Audit trail:** Weekly settlements require transparent, unalterable records of each order, payment, producer share and commission, suitable for producers' tax reporting and BRFN's accounts. Financial records are generally kept for at least six years.
- **VAT:** Many foods are zero-rated and others are not, and commission may be subject to VAT. VAT treatment should be recorded per item and commission recorded separately, with the correct treatment to be confirmed by the company's finance team.

---

## 3. Social Considerations

- **Producers with varied technical ability:** Some producers currently work by email and telephone. Order notifications that result from checkout (including the 48-hour lead time) should be available through simple channels, such as email summaries and printable order lists, so smaller producers are not disadvantaged.
- **Customer segments:** Young professionals and families, community groups (schools, care facilities, voluntary groups) and restaurants have different needs. Itemised, per-producer receipts support organisations that need records for catering budgets. Checkout should be clear and usable on mobile and desktop and with assistive technology.
- **Clarity in multi-vendor orders:** Customers need to understand that one basket may produce several deliveries or collection slots and who is responsible for each. Clear communication reduces confusion, missed collections and complaints.
- **Tone around payment problems:** Declined payments can cause embarrassment or worry. Messages should be neutral and offer clear next steps, such as retrying or using another method.
- **Fairness to producers:** The 48-hour notice and accurate stock handling protect producers from short-notice demands and from being credited for orders they cannot fulfil.
- **Access across the 20-mile area:** Delivery and collection options and any charges should be visible before confirmation so customers outside the city centre are not surprised by costs.

---

## 4. Ethical Considerations

- **Honest stock information:** The stock check at checkout and a short reservation during payment prevent customers being told an item is available when it is not. This also prevents producers being committed to orders they cannot meet.
- **Transparent commission and payment split:** The 5% commission and each producer's share must be clear in producer terms and visible in settlement statements, and customers should not be misled about where their money goes.
- **No manipulative design:** The confirmation step should show the full total, producer breakdown and delivery arrangements without pre-selected extras, hidden fees or misleading timers.
- **Fair handling of failures:**
  - *Declined payment:* the customer keeps their basket and can retry without blame.
  - *Payment service unavailable:* a controlled retry or pending state with clear communication, rather than failing silently or leaving the customer unsure whether they have been charged.
  - *No double charging:* retries must not result in duplicate payments, and any error needs a clear refund route.
- **Allergen and food safety information:** This is safety-critical. It must be accurate, prominent and carried through to the order record, even if this adds steps for producers.
- **Responsible use of data:** Customer purchase data is used only for fulfilment, payment, support and traceability, and is not shared with producers beyond what each needs, nor sold to third parties.
- **Equal treatment of producers:** System failures (for example delayed inventory updates) should not unfairly penalise individual producers, and one producer's data should not be exposed to another.

---

## 5. Professional Considerations

As a development team working for a company, we are accountable to the client, to users and to the public.

- **Professional conduct (BCS Code of Conduct):** Act in the public interest, work within our competence, be honest about what the system can and cannot do, and respect confidentiality. Where payment regulation, food law or tax treatment is beyond the team's expertise, it should be referred to legal or finance specialists rather than assumed.
- **Meeting stakeholder requirements:** The system must support the stated requirements: stock validation, multi-vendor order splitting, automatic 5% commission calculation, producer notification with 48 hours' lead time and settlement records suitable for audit.
- **Secure development:**
  - Validate prices, quantities and totals on the server, never trusting values sent from the browser.
  - Protect against common vulnerabilities (OWASP Top 10): injection, cross-site scripting, CSRF and broken access control.
  - Keep API keys and secrets out of source control.
  - Avoid logging card data or unnecessary personal data.
- **Reliability under concurrency:** Handle simultaneous checkouts safely (for example with transactional stock updates or reservations) so that two customers cannot buy the last item.
- **Testing of all paths:** Normal purchase, insufficient stock, payment success, payment declined and retried, payment service unavailable, and multi-vendor splitting. This includes commission and rounding edge cases (single vs multiple producers, delivery fees, mixed VAT items).
- **Documentation and traceability:** Maintain traceability from requirements to design, code and tests, and document the payment states, exception paths and assumptions (such as the use of a sandbox provider and the payment-regulation assumption above).
- **Teamwork and process:** Use version control, code review and agreed responsibilities. Record decisions and risks so that the work can be audited and maintained by others.

---

## 6. Key Risks and Mitigations

| Risk | Category | Mitigation |
|---|---|---|
| Customer data shared with producers beyond what is needed | Legal / Ethical | Split order data per producer, role-based access, DPIA |
| Card data stored or mishandled | Legal / Professional | Tokenised sandbox payment only, no card data stored |
| Customer charged twice after retry or outage | Ethical / Professional | Idempotency keys, defined payment states, reconciliation, refund process |
| Overselling or inaccurate stock | Legal / Ethical | Server-side stock check at checkout, short reservation, honest messaging |
| Unclear responsibility in multi-vendor orders | Legal / Social | Producer-separated order elements, itemised confirmation, clear terms |
| Commission or VAT miscalculated | Legal / Professional | Decimal arithmetic, documented rounding, automated tests, audit trail |
| Missing allergen or best-before information in order record | Legal / Ethical | Carry product food information into the order record, mandatory fields |
| Small producers miss orders due to limited technical ability | Social | Simple email and printable notifications, 48-hour lead time enforced |
| Hidden fees or confusing confirmation step | Ethical / Legal | Full price breakdown and arrangements shown before confirming |

---

## 7. Conclusion

The project brings together payment, personal data, food information and multi-party commercial relationships. The team's responsibilities are to protect customer and producer data, process payments securely through a regulated sandbox provider, provide clear and honest information at checkout, calculate and record commission and producer shares accurately, and handle failures fairly. Working to professional standards of security, testing and documentation supports trust in the marketplace among producers, customers, community groups and restaurants.

---

## References (verify current versions)

- UK GDPR and Data Protection Act 2018; ICO guidance
- Payment Services Regulations 2017; PCI Security Standards Council, *PCI DSS*
- Consumer Rights Act 2015
- Consumer Contracts (Information, Cancellation and Additional Charges) Regulations 2013
- Electronic Commerce (EC Directive) Regulations 2002
- Digital Markets, Competition and Consumers Act 2024
- Food Information Regulations 2014; Regulation (EC) 178/2002 as retained in UK law
- BCS, *Code of Conduct for BCS Members*
- OWASP, *Top 10*
