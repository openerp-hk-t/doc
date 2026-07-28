---
title: Overview
category: Features
order: 1
---


## Overview

UML Copilot consists of a conversation panel on the left, a model canvas in the center, and a toolbar at the top.

### Core Capabilities

#### Excel / CSV Automatic Modeling

After importing an Excel or CSV file, the system can automatically perform the following tasks:

- Identify worksheets
- Generate data tables
- Identify field names
- Infer field types
- Detect primary keys
- Detect foreign-key candidates
- Infer relationships between tables
- Automatically arrange the UML model

#### Natural-Language Editing

Users can describe changes directly in the conversation panel. The system converts those instructions into structured model updates.

Typical supported operations include:

- Add, delete, or rename tables
- Add, delete, or rename fields
- Change field types
- Define primary keys
- Define foreign keys
- Create or remove field relationships
- Change relationship types
- Adjust the model layout

#### Visual UML Canvas

The canvas displays each data table as an individual card.

A table card typically contains:

- Table name
- Primary-key fields
- Foreign-key fields
- Regular fields
- Field types
- Relationship lines
- Relationship cardinalities

Supported relationship types include:

- One-to-one
- One-to-many
- Many-to-one
- Many-to-many
- Self-referencing relationships

#### Model Export

Completed models can be exported as:

- JSON
- Mermaid
- Data model documentation
- Extensible SQL, ORM, or Odoo model code

### Interface Areas

| Area | Main Functions |
|---|---|
| Top toolbar | View table and relationship counts, undo changes, switch languages, and export JSON or Mermaid |
| Left import area | Upload Excel or CSV files |
| Left conversation panel | Add, modify, or delete model content using natural language |
| Central canvas | Display tables, fields, primary keys, foreign keys, and relationships |
| Canvas controls | Zoom, reset, lock, or adjust the view |
| Version history | View and switch between different model versions |
| Minimap | Quickly navigate between areas in a large model |
