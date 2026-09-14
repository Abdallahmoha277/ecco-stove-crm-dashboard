# Data Dictionary

This document describes the main fields used in the Ecco Stove CRM
and explains their purpose within the data model.

## Customers

| Field | Description | Data Type |
|---|---|---|
| Customer_ID | Unique identifier for each customer | Text |
| Customer_Name | Customer's full name | Text |
| Email | Customer email address | Text |
| Phone | Customer phone number | Text |
| Country | Customer country | Text |
| Customer_Type | Type of customer, such as Homeowner, Dealer, Installer, Architect or Commercial | Text |
| Data_Quality_Status | Indicates whether the customer record passed data-quality checks | Text |

## Leads

| Field | Description | Data Type |
|---|---|---|
| Lead_ID | Unique identifier for each lead | Text |
| Customer_ID | Links the lead to a customer | Text |
| Lead_Date | Date when the lead was created | Date |
| Lead_Source | Source through which the lead was generated | Text |
| Product_ID | Product associated with the lead | Text |
| Product_Name | Product associated with the lead | Text |
| Sales_Stage | Current stage of the sales process | Text |
| Lead_Score | Score assigned according to the sales stage | Number |
| Estimated_Value | Estimated commercial value of the lead | Currency |
| Owner | Person responsible for the lead | Text |
| Next_Follow_Up | Planned follow-up date | Date |
| Campaign_ID | Links the lead to a marketing campaign | Text |

## Products

| Field | Description | Data Type |
|---|---|---|
| Product_ID | Unique product identifier | Text |
| Product_Name | Ecco Stove product name | Text |
| Product_Category | Product category | Text |
| Description | Product description | Text |

## Activities

| Field | Description | Data Type |
|---|---|---|
| Activity_ID | Unique activity identifier | Text |
| Customer_ID | Customer associated with the activity | Text |
| Lead_ID | Lead associated with the activity | Text |
| Activity_Date | Date of the activity | Date |
| Activity_Type | Type of customer interaction | Text |
| Subject | Purpose or subject of the activity | Text |
| Outcome | Result of the activity | Text |
| Next_Action | Planned next action | Text |
| Next_Action_Date | Date of the next planned action | Date |
| Assigned_To | Person responsible for the activity | Text |

## Opportunities

| Field | Description | Data Type |
|---|---|---|
| Opportunity_ID | Unique opportunity identifier | Text |
| Lead_ID | Lead associated with the opportunity | Text |
| Customer_ID | Customer associated with the opportunity | Text |
| Product_ID | Product associated with the opportunity | Text |
| Product_Name | Product associated with the opportunity | Text |
| Opportunity_Name | Name of the sales opportunity | Text |
| Pipeline_Stage | Current opportunity stage | Text |
| Amount | Potential opportunity value | Currency |
| Probability | Estimated probability of winning the opportunity | Percentage |
| Expected_Value | Probability-weighted opportunity value | Currency |
| Expected_Close_Date | Expected closing date | Date |
| Owner | Person responsible for the opportunity | Text |
| Lead_Date | Original lead creation date | Date |

## Marketing Campaigns

| Field | Description | Data Type |
|---|---|---|
| Campaign_ID | Unique campaign identifier | Text |
| Campaign_Name | Name of the marketing campaign | Text |
| Campaign_Channel | Marketing channel used | Text |
| Campaign_Type | Type of campaign | Text |
| Start_Date | Campaign start date | Date |
| End_Date | Campaign end date | Date |
| Budget | Campaign budget | Currency |
| Campaign_Duration_Days | Campaign duration in days | Number |
| Campaign_Status | Current campaign status | Text |

## Data Model Relationships

The CRM uses the following relationships:

- Customers → Leads: one-to-many
- Products → Leads: one-to-many
- Leads → Activities: one-to-many
- Leads → Opportunities: one-to-many
- Marketing Campaigns → Leads: one-to-many

## Data Quality

Power Query was used to standardize and validate the CRM data,
including text cleaning, country normalization, product normalization,
duplicate detection and removal, and missing-value handling.

The dataset is synthetic and contains no real customer personal information.
