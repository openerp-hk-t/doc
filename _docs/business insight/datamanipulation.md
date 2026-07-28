---
title: Field Relationships
category: Features
order: 4
---


## Field Relationships

Field relationships describe data dependencies between tables.

### Primary Keys and Foreign Keys

A primary key uniquely identifies a record.

Example:

```text
Users.user_id
```

A foreign key references the primary key of another table.

Example:

```text
Orders.user_id -> Users.user_id
```

This relationship means that each order belongs to one user.

### One-to-One Relationships

One record in the primary table corresponds to at most one record in the related table.

Example:

```text
Users.user_id -> User_Profile.user_id
```

Typical use cases:

- User and user profile
- Employee and employee extension information
- Order and unique invoice

Natural-language instruction:

```text
Define a one-to-one relationship between Users.user_id and User_Profile.user_id.
```

### One-to-Many Relationships

One record in the primary table can correspond to multiple records in the related table.

Example:

```text
Users.user_id -> Orders.user_id
```

This means that one user can have multiple orders.

```text
Orders.order_id -> Order_Items.order_id
```

This means that one order can contain multiple order items.

Natural-language instruction:

```text
Create a one-to-many relationship between Users and Orders using Users.user_id and Orders.user_id.
```

### Many-to-One Relationships

A many-to-one relationship is the reverse perspective of a one-to-many relationship.

Examples:

```text
Multiple Orders records -> One Users record
```

```text
Multiple Products records -> One Categories record
```

Natural-language instruction:

```text
Set Products.category_id as a foreign key referencing Categories.category_id.
```

### Many-to-Many Relationships

A many-to-many relationship is normally implemented through a junction table.

For example, Orders and Products are connected through `Order_Items`:

```text
Orders
  |
  | 1:N
  |
Order_Items
  |
  | N:1
  |
Products
```

Corresponding fields:

```text
Order_Items.order_id -> Orders.order_id
Order_Items.product_id -> Products.product_id
```

Natural-language instruction:

```text
Use Order_Items as the junction table to create a many-to-many relationship between Orders and Products.
```

### Self-Referencing Relationships

A table can also reference itself.

Example of a category hierarchy:

```text
Categories.parent_id -> Categories.category_id
```

This means that a category can have one parent category and multiple child categories.

Natural-language instruction:

```text
Link Categories.parent_id to Categories.category_id to create a hierarchical category structure.
```

### Relationship Detection Rules

The system can infer relationships from the following characteristics:

- Matching field names
- Fields ending in `_id`
- Foreign-key names that correspond to table names
- Clear value containment between two columns
- Semantic correspondence between worksheet names and field names

Example:

```text
Orders.user_id
Users.user_id
```

The system may infer:

```text
Orders.user_id -> Users.user_id
```

### Relationship Design Recommendations

When creating relationships, ensure that:

- Primary-key and foreign-key types are consistent
- Foreign-key names have clear business meaning
- Duplicate relationships are not created
- Many-to-many relationships use a junction table
- Unstable business fields are not used as relationship keys
- Existing relationships are reviewed before deleting a field
- Foreign keys are updated when a referenced primary key is renamed

---
