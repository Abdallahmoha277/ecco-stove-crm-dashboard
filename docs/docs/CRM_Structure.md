# CRM Structure

This document describes the structure of the Ecco Stove CRM data model
and the relationships between its main entities.

## Data Model Overview

```text
Customers
    │
    │ Customer_ID
    ↓
  Leads
   ↙   ↘
  ↓     ↓
Activities  Opportunities

Products
    │
    │ Product_ID
    ↓
  Leads

Marketing_Campaigns
    │
    │ Campaign_ID
    ↓
  Leads```
Main CRM Tables
Customers

Stores the core customer information, including customer identity,
contact information, country and customer type.

Leads

Stores potential sales opportunities and tracks the customer's
progress through the sales process.

Products

Contains the Ecco Stove products and their related product information.

Activities

Records interactions and follow-up activities related to leads,
such as emails, phone calls, meetings and site surveys.

Opportunities

Tracks potential sales opportunities, including pipeline stage,
opportunity amount, probability and expected value.

Marketing Campaigns

Stores information about marketing campaigns and connects campaigns
to the leads they generate.

Relationships

The data model uses the following one-to-many relationships:

Parent Table	Child Table	Key
Customers	Leads	Customer_ID
Products	Leads	Product_ID
Leads	Activities	Lead_ID
Leads	Opportunities	Lead_ID
Marketing_Campaigns	Leads	Campaign_ID
Why This Data Model?

The data model was designed to separate different CRM entities while
maintaining clear relationships between them.

Customers represent the people or organizations, while Leads represent
their sales enquiries and progression through the sales pipeline.

Activities are connected to Leads so that customer interactions and
follow-ups can be tracked throughout the sales process.

Opportunities are connected to Leads to allow potential revenue,
probability and expected pipeline value to be analysed.

Products and Marketing Campaigns are connected to Leads so that the
business can analyse which products generate demand and which marketing
channels or campaigns generate leads.

This structure reduces unnecessary duplication, improves data
consistency and allows CRM information to be analysed through
Power Pivot, PivotTables and the interactive dashboard.

Data Flow

The overall data flow is:

Raw Customer Data
        ↓
    Power Query
        ↓
Clean CRM Tables
        ↓
    Data Model
        ↓
  Pivot Analysis
        ↓
 Interactive Dashboard
Technologies Used
Microsoft Excel
Power Query
Power Pivot
DAX
PivotTables
PivotCharts
Data Modelling
