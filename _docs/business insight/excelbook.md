---
title: Excel Workbook
category: Features
order: 3
---

## Building the Excel Workbook

To improve recognition accuracy, prepare the Excel file according to a consistent structure before importing it.

### S.1 Recommended Structure

The recommended convention is:

> One worksheet represents one data table.

Example workbook:

```text
ecommerce_model.xlsx
├── Users
├── User_Address
├── Categories
├── Products
├── Orders
├── Order_Items
├── Payments
└── Logistics
```

The worksheet name is used as the default table name.

### S.2 Column Headers

The first row of each worksheet should contain field names. Sample data should begin from the second row.

#### Users Worksheet

| user_id | username | email | phone | level | created_at |
|---:|---|---|---|---|---|
| 1 | Alice | alice@example.com | 13800000001 | VIP | 2026-07-01 |
| 2 | Bob | bob@example.com | 13800000002 | Normal | 2026-07-02 |

#### Orders Worksheet

| order_id | user_id | address_id | order_time | total_amount | status |
|---:|---:|---:|---|---:|---|
| 10001 | 1 | 101 | 2026-07-10 10:30:00 | 299.00 | paid |
| 10002 | 2 | 102 | 2026-07-11 14:20:00 | 499.00 | shipped |

### S.3 Table Naming Conventions

Use one consistent naming style, such as:

```text
Users
User_Address
Order_Items
```

or:

```text
users
user_address
order_items
```

Recommendations:

- Use English names
- Avoid spaces
- Avoid special characters
- Keep singular/plural conventions consistent
- Avoid mixing Chinese, English, and pinyin
- Use names that clearly describe the business entity

Not recommended:

```text
Table1
Sheet1
User Table
order-items!
```

### S.4 Field Naming Conventions

The lowercase snake_case convention is recommended:

```text
user_id
product_name
order_time
total_amount
created_at
```

Recommendations:

- Name a primary key as `singular_table_name_id`
- Keep foreign-key names consistent with the referenced primary key
- Use `_time`, `_date`, or `_at` for date and time fields
- Use `status` consistently for status fields
- Use `is_`, `has_`, or `enable_` prefixes for Boolean fields

Examples:

```text
is_default
is_active
has_invoice
created_at
updated_at
```

### S.5 Field Type Inference

The system infers field types from the content in Excel.

| Excel Content | Recommended Inferred Type |
|---|---|
| 1, 2, 3 | integer |
| 12.5, 299.00 | decimal / float |
| User names, addresses, descriptions | string / text |
| 2026-07-24 | date |
| 2026-07-24 10:30:00 | datetime |
| TRUE / FALSE | boolean |

To avoid incorrect inference, sample values within the same column should use a consistent data type.

Not recommended:

| amount |
|---|
| 100 |
| 200.5 |
| N/A |
| Undetermined |

Recommended:

| amount |
|---:|
| 100.00 |
| 200.50 |
| 0.00 |
| 350.00 |

### S.6 Primary-Key Design

Each table should have a unique primary key.

Examples:

```text
Users.user_id
Products.product_id
Orders.order_id
Payments.payment_id
```

A primary key should be:

- Unique
- Non-null
- Type-stable
- Unlikely to change with business content

Names, phone numbers, and product names should not normally be used directly as primary keys.

### S.7 Null Values and Sample Data

The system may use sample data to infer field types and relationships. Each worksheet should therefore contain approximately 2–10 valid sample rows.

Important guidelines:

- Do not merge cells
- Do not place description rows above the header
- Do not place multiple independent tables in one worksheet
- Do not use colors as the only representation of field meaning
- Do not insert summary or total rows in the data area
- Avoid completely empty columns
- Use a consistent date format

### S.8 Multi-Worksheet Excel Example

```text
Users
  user_id
  username
  email

Products
  product_id
  category_id
  product_name
  price

Orders
  order_id
  user_id
  order_time
  total_amount

Order_Items
  item_id
  order_id
  product_id
  quantity
  unit_price
```

After import, the system can generate a model containing relationships among users, products, orders, and order items.

