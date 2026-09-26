# 🛒 Cart Abandonment Pattern Analysis  
## 📊 Power BI Dashboard

The interactive Power BI dashboard provides an overview of cart abandonment patterns, session behavior, product activity, price ranges, brands, and event types.

![Cart Abandonment Dashboard](screenshots/Cart_dashboard.png)

## 📌 Project Overview

Cart abandonment is a major challenge in e-commerce. Users may browse products, add items to their shopping cart, but leave without completing a purchase.

This project analyzes e-commerce clickstream data to identify patterns associated with cart abandonment and understand user shopping behavior.

The project follows an end-to-end data analytics workflow using:

- 🐍 Python for data cleaning and exploratory data analysis
- 🗄️ MySQL for structured data storage and SQL analysis
- 📊 Power BI for interactive dashboard development
- 📈 DAX for KPI and analytical measures

The analysis focuses on **session-level cart behavior**, allowing cart abandonment to be measured based on complete shopping sessions rather than individual events.

---

# 🎯 Business Objective

The main objective of this project is to answer:

> **What patterns are associated with users abandoning their shopping carts without completing a purchase?**

The analysis investigates:

- How many sessions resulted in cart activity?
- How many cart sessions were converted?
- How many cart sessions were abandoned?
- What is the cart abandonment rate?
- How does abandonment vary across price ranges?
- How does session duration differ between abandoned and converted sessions?
- How does abandonment vary across brands?
- What types of events dominate user activity?
- Which individual products have higher observed abandonment?

---

# 📊 Dataset

The project uses an e-commerce clickstream dataset containing user interaction events.

### Dataset columns

| Column | Description |
|---|---|
| `event_time` | Timestamp of the user event |
| `event_type` | Type of event such as view, cart, or purchase |
| `product_id` | Unique product identifier |
| `category_id` | Product category identifier |
| `category_code` | Product category |
| `brand` | Product brand |
| `price` | Product price |
| `user_id` | Unique user identifier |
| `user_session` | Identifier representing a shopping session |

The original October dataset contains millions of events and is large enough that processing the complete dataset directly on a 16 GB RAM system is inefficient for this project.

Therefore, a **complete-session sampling approach** was used.

---

# 🔬 Sampling Methodology

Instead of randomly sampling individual event rows, complete shopping sessions were sampled.

### Process

1. The October dataset was scanned to identify unique `user_session` IDs.
2. The dataset contained approximately **9.24 million unique sessions**.
3. **20,000 complete sessions** were randomly selected using a fixed random seed.
4. All events belonging to those selected sessions were extracted.
5. Duplicate event rows were removed.
6. The final analytical dataset contained:

```text
20,000 unique sessions
93,014 events
19,796 unique users
