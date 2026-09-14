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
  Leads
