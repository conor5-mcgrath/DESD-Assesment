# Bristol Regional Food Network - Digital Marketplace
## Stakeholder Analysis

### 1. Project Overview

The Bristol Regional Food Network Digital Marketplace is a platform designed to connect customers with local food producers. Customers will be able to browse and search for products, add items from multiple producers to a basket, complete checkout using a simulated payment service, and receive order and delivery or collection confirmations.

The project is divided into four core modules:

1. Product exploration and searching
2. Basket management
3. Order confirmation
4. Delivery confirmation

The system will support multi-producer orders, stock validation, simulated payment processing, producer-specific order management, and the automatic calculation of the marketplace's 5% commission.

### 2. Stakeholder Identification and Analysis

| Stakeholder | Role and Responsibilities | Main Interests |
|---|---|---|
| Project Supervisor | Provides academic guidance, reviews project progress, and gives feedback on deliverables. | Project quality, assessment criteria, progress, and achievement of objectives. |
| Project Manager and Developer | Manages the project, coordinates tasks, monitors deadlines, communicates with the supervisor, and contributes to software development and testing. | Successful project delivery, effective teamwork, meeting deadlines, and software quality. |
| Developer 2 | Contributes to the design, implementation, integration, and testing of the marketplace. Initial focus: product exploration and searching. | Clear requirements, functional features, and maintainable code. |
| Developer 3 | Contributes to the design, implementation, integration, and testing of the marketplace. Initial focus: basket management. | Correct basket calculations, stock validation, and integration with other modules. |
| Developer 4 | Contributes to the design, implementation, integration, and testing of the marketplace. Initial focus: order confirmation and delivery confirmation. | Reliable order processing, simulated payments, and clear confirmation workflows. |
| Customers | Search for products, manage baskets, purchase from multiple producers, and receive order information. | Ease of use, accurate product availability, transparent pricing, and clear delivery or collection arrangements. |
| Food Producers | Provide product information, maintain stock information, receive confirmed orders, and fulfil purchases. | Accurate order details, clear fulfilment responsibilities, and sufficient preparation time. |
| Payment Service | Provides simulated payment authorisation and returns successful, declined, or temporarily unavailable responses. | Correct payment requests, safe testing, and appropriate handling of payment outcomes. |

### 3. Stakeholder Needs and Expectations

#### Customers

Customers require an intuitive marketplace where they can browse and search for products, add items from different producers to one basket, review prices, and understand the relevant delivery or collection arrangements.

The system must validate stock before checkout and explain when a product is unavailable or the requested quantity cannot be fulfilled. Customers must also receive clear payment and order confirmation messages.

#### Food Producers

Producers require accurate product and inventory information, clear visibility of their own confirmed order items, and notifications that allow them to prepare orders appropriately.

The system should maintain separate producer-specific order elements within an overall marketplace order. Where fulfilment scheduling is implemented, the system should account for the required minimum 48-hour preparation lead time.

#### Project Supervisor

The supervisor provides academic guidance and feedback to help ensure that the project meets its objectives and assessment requirements.

Supervisor meetings will take place either during every weekly stand-up or at the end of every sprint, depending on the agreed supervision arrangement.

#### Project Manager and Developers

The project team requires clear requirements, a prioritised product backlog, manageable tasks, regular communication, and a shared understanding of module interfaces.

The project manager will also contribute directly to development. All five team members will remain involved throughout the project, including integration, testing, documentation, and reviews.

#### Payment Service

The payment service must support simulated successful payments, declined payments, and temporary service failures.

The implementation must use a sandbox or mock payment gateway and must not process live payments or real financial data.

### 4. Team Structure and Responsibilities

The project will use the same five-person team throughout development.

| Team Role | Main Responsibilities |
|---|---|
| Project Supervisor | Academic guidance, feedback, and project reviews. |
| Project Manager and Developer | Project planning, task allocation, deadline monitoring, development, integration, and testing. |
| Developer 2 | Initial focus on product exploration and searching. |
| Developer 3 | Initial focus on basket management and stock validation. |
| Developer 4 | Initial focus on order confirmation and delivery confirmation. |

The initial module allocations are intended to organise the work rather than create strict boundaries. All developers will collaborate on integration, code reviews, testing, documentation, and resolving technical issues.

The project manager will contribute to both project management and software development.

### 5. Stakeholder Communication Plan

| Stakeholder | Communication Method | Frequency |
|---|---|---|
| Project Supervisor | Progress discussions, feedback, and project reviews. | Either every weekly stand-up or at the end of every sprint, as agreed. |
| Project Manager and Developers | Team stand-ups, task tracking, and collaborative discussions. | Weekly, with additional communication when required. |
| Customers | Requirements discussions and usability feedback, where available. | During requirements gathering and testing. |
| Food Producers | Requirements discussions and feedback on product and order workflows. | During requirements gathering and relevant reviews. |
| Payment Service | Technical documentation and sandbox testing. | During implementation and testing. |

### 6. Key Stakeholder Risks

- **Unclear requirements:** Agree on expected functionality and acceptance criteria before implementation.
- **Uneven workloads:** Monitor task progress and redistribute work when necessary.
- **Stock inaccuracies:** Validate current stock quantities before checkout and account for concurrent purchases.
- **Payment failures:** Provide clear error messages, safe retries, and appropriate recovery for temporary service failures.
- **Integration problems:** Agree on data structures and module interfaces early and test integration regularly.
- **Limited producer technical experience:** Keep producer-facing order information simple and understandable.
- **Insufficient preparation time:** Account for the minimum 48-hour preparation requirement wherever fulfilment scheduling is included in scope.

### 7. Conclusion

The stakeholder analysis identifies the people and systems that influence the successful delivery of the Bristol Regional Food Network Digital Marketplace.

Customers and producers are the main operational stakeholders. The project supervisor provides academic oversight, while the project manager coordinates the work and contributes to development.

The five-person team will work collaboratively throughout the project to deliver the four core modules, with particular attention to stock validation, multi-producer orders, simulated payments, and clear order and fulfilment confirmations.
