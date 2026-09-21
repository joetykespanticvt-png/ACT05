# Week 3: User Stories, Acceptance Criteria & Backlog Management
**System Name:** E-Commerce Grocery Delivery System  
**Course:** Software Engineering / Systems Analysis & Design  

---

## 👥 Team Members & Task Delegation

| Team Member | Role | Assigned Modules & User Stories |
| :--- | :--- | :--- |
| **Member 1** | Backend & Inventory Lead | US-04 (Payment Integration), US-06 (Catalog & Inventory) |
| **Member 2** | Frontend & Storefront Lead | US-01 (Search & Filter), US-02 (Cart Management), US-03 (Checkout) |
| **Member 3** | Mobile & Order Tracking Lead | US-05 (Real-Time Tracking), US-07 (Admin Assignment), US-08 (Driver Delivery) |
| **Member 4** | QA & Review Module Lead | US-09 (Ratings & Reviews), Board Setup & QA Verification |

---

## 📜 User Stories & Acceptance Criteria

### US-01: Product Search & Filtering
* **User Story:** As a **Customer**, I want to **search for products by keyword and filter by category, price, or stock availability** so that **I can quickly find the groceries I need**.
* **Acceptance Criteria (BDD):**
  * **Given** a customer is on the homepage or product catalog page, **When** they enter a keyword into the search bar and press enter, **Then** the system displays all matching products containing that keyword.
  * **Given** search or browse results are displayed, **When** the customer selects a category filter (e.g., "Dairy") or sets a maximum price threshold, **Then** the result list updates in real time to show only items matching the active filters.
  * **Given** an item is out of stock, **When** the customer filters by "In Stock Only", **Then** the out-of-stock items are hidden from the result view.

---

### US-02: Shopping Cart Management
* **User Story:** As a **Customer**, I want to **add, adjust quantities of, or remove items in my shopping cart** so that **I can curate my purchase before checking out**.
* **Acceptance Criteria (BDD):**
  * **Given** a customer is viewing a product with 5 units available in stock, **When** they click "Add to Cart", **Then** the item is added to their active cart and the cart counter increments.
  * **Given** an item is in the customer's cart, **When** they increase the quantity past 5 units (exceeding stock), **Then** the system prevents the addition and displays an error message: *"Requested quantity exceeds available stock."*
  * **Given** an item is in the cart, **When** the customer clicks "Remove", **Then** the item is removed and the cart total updates immediately.

---

### US-03: Order Checkout & Totals
* **User Story:** As a **Customer**, I want to **select a delivery address, choose a preferred time slot, and review order totals** so that **I can finalize my grocery order**.
* **Acceptance Criteria (BDD):**
  * **Given** a logged-in customer with items in their cart, **When** they proceed to checkout, **Then** they can choose an existing delivery address or add a new one.
  * **Given** valid delivery details are selected, **When** the checkout page loads, **Then** the system displays an itemized summary showing the subtotal, delivery fee, taxes, applied discounts, and final total.
  * **Given** a customer is not logged in, **When** they click "Proceed to Checkout", **Then** the system redirects them to the Login/Register page before allowing order completion.

---

### US-04: Payment Gateway Integration
* **User Story:** As a **Customer**, I want to **pay for my order using a secure payment method** so that **my order can be confirmed and processed**.
* **Acceptance Criteria (BDD):**
  * **Given** a customer is on the payment step, **When** they submit valid credit card/payment details, **Then** the system sends the payment to the Payment Gateway and receives a "Success" response.
  * **Given** a successful payment response, **When** the order is created, **Then** the order status is set to `Confirmed`, inventory is immediately reduced, and a receipt is displayed.
  * **Given** a payment attempt fails or is declined, **When** the Payment Gateway returns an error, **Then** the order remains `Pending` and the customer is prompted to retry or change payment methods.

---

### US-05: Real-Time Order Tracking
* **User Story:** As a **Customer**, I want to **view real-time status updates of my active order** so that **I know when my groceries will arrive**.
* **Acceptance Criteria (BDD):**
  * **Given** a customer has an active order, **When** they open the "My Orders" tab, **Then** they see the current order status (`Pending`, `Confirmed`, `Preparing`, `Out for Delivery`, or `Delivered`).
  * **Given** an order status changes to `Out for Delivery`, **When** the customer views the tracking page, **Then** they see the assigned delivery personnel's contact details and estimated arrival time.

---

### US-06: Product Catalog & Inventory Management
* **User Story:** As an **Administrator**, I want to **add, edit, and update stock levels for grocery products** so that **customers have accurate pricing and availability details**.
* **Acceptance Criteria (BDD):**
  * **Given** an authenticated admin in the Admin Dashboard, **When** they enter product details (name, category, price, stock quantity, image) and click "Save", **Then** the product is published to the customer catalog.
  * **Given** a product's price or stock level changes, **When** the admin updates the inventory count and saves, **Then** the new values immediately reflect across the customer portal.

---

### US-07: Admin Order Assignment
* **User Story:** As an **Administrator**, I want to **view new customer orders and assign them to available delivery personnel** so that **fulfillment can begin quickly**.
* **Acceptance Criteria (BDD):**
  * **Given** a new order with status `Confirmed`, **When** the admin reviews the order in the management console, **Then** they can change the status to `Preparing`.
  * **Given** an order is prepared, **When** the admin selects an available delivery driver from the dropdown and clicks "Assign", **Then** the driver receives a notification and the order transitions to `Out for Delivery`.

---

### US-08: Delivery Driver Execution
* **User Story:** As a **Delivery Driver**, I want to **view my assigned deliveries and update status upon completion** so that **the system and customer stay informed**.
* **Acceptance Criteria (BDD):**
  * **Given** a delivery driver logged into the mobile app, **When** an order is assigned to them, **Then** it appears on their active delivery list with customer address and contact details.
  * **Given** the driver delivers the groceries to the customer, **When** they tap "Mark as Delivered", **Then** the order status permanently changes to `Delivered` and a delivery confirmation timestamp is logged.

---

### US-09: Customer Product Reviews & Ratings
* **User Story:** As a **Customer**, I want to **rate and review products from my completed orders** so that **I can share feedback with other shoppers and the store**.
* **Acceptance Criteria (BDD):**
  * **Given** an order with status `Delivered`, **When** the customer views the completed order, **Then** a "Rate & Review" option becomes enabled.
  * **Given** the customer submits a 1–5 star rating and text feedback, **When** they click "Submit Review", **Then** the review is attached to the product page and average rating scores recalculate.

---

## 📊 Story Point Estimation Matrix (Planning Poker)

Story Points assigned using the standard Fibonacci sequence ($1, 2, 3, 5, 8, 13$) based on complexity, effort, and risk:

| Story ID | Story Title | Points | Justification |
| :--- | :--- | :---: | :--- |
| **US-01** | Product Search & Filtering | **3** | Moderate UI work with basic query filtering; low architecture risk. |
| **US-02** | Shopping Cart Management | **3** | Client-side/session state handling, logic validation against available stock. |
| **US-03** | Order Checkout & Totals | **5** | Multi-step workflow involving dynamic calculations (tax, delivery fees, discounts, addresses). |
| **US-04** | Payment Gateway Integration | **8** | High technical complexity, third-party API integration, webhook verification, PCI/security considerations. |
| **US-05** | Real-Time Order Tracking | **5** | Polling/WebSocket logic and progress status rendering on frontend. |
| **US-06** | Admin Catalog & Inventory | **3** | Standard CRUD backend functionality and image upload handling. |
| **US-07** | Admin Order Assignment | **3** | Relational updates between Order models and Delivery Personnel entities. |
| **US-08** | Delivery Driver Execution | **2** | Basic status flag updates and simple mobile list view; low risk. |
| **US-09** | Product Reviews & Ratings | **2** | Simple relational store with basic mathematical average aggregation. |

---

## 🚀 Sprint 1 vs. Product Backlog Breakdown

### Sprint 1 Scope (Target: 16 Story Points)
*Focus: Establish core purchasing loop, product catalog baseline, and order fulfillment updates.*

* **US-06:** Product Catalog & Inventory Management (**3 pts**) — *Member 1*
* **US-01:** Product Search & Filtering (**3 pts**) — *Member 2*
* **US-02:** Shopping Cart Management (**3 pts**) — *Member 2*
* **US-03:** Order Checkout & Totals (**5 pts**) — *Member 2*
* **US-08:** Delivery Driver Execution (**2 pts**) — *Member 3*

### Product Backlog (Future Sprints - 18 Story Points)
* **US-04:** Payment Gateway Integration (**8 pts**) — *Member 1*
* **US-05:** Real-Time Order Tracking (**5 pts**) — *Member 3*
* **US-07:** Admin Order Assignment (**3 pts**) — *Member 3*
* **US-09:** Customer Product Reviews & Ratings (**2 pts**) — *Member 4*

---

## 📌 Project Board Link
* **GitHub Project Board:** `[https://github.com/users/joetykespanticvt-png/projects/1]`
