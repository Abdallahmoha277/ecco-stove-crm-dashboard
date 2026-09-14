````markdown
# Data Cleaning

This document describes the data cleaning and transformation process used to prepare the Ecco Stove CRM dataset for analysis.

## Data Source

The original customer dataset was stored in the `Raw_Customer_Data` table.

The raw dataset contained 153 records, including 150 unique customer records and 3 intentional duplicate records created to demonstrate the data cleaning process.

The `Raw_Customer_Data` table was kept unchanged as the source layer.

## Data Cleaning Process

Power Query was used to transform the raw data into structured CRM tables.

The main cleaning steps were:

1. Text cleaning and standardization
2. Country normalization
3. Product name normalization
4. Sales stage standardization
5. Missing-value handling
6. Duplicate detection and removal
7. Data type conversion
8. Data quality classification
9. Creation of calculated CRM fields

## Text Cleaning

Text fields were cleaned using trimming and text-cleaning operations.

This helped remove unnecessary spaces and improve consistency across records.

For example:

- `UK ` was standardized to `UK`
- Inconsistent text formatting was normalized
- Empty or missing values were preserved where appropriate for data-quality analysis

## Country Standardization

Country values were standardized to maintain consistent reporting.

For example:

```text
United Kingdom
UK
UK 
````

were normalized to:

```text
UK
```

This ensures that the same country is not treated as multiple categories in PivotTables and dashboard analysis.

## Product Standardization

Product names were standardized to ensure consistent product analysis.

For example:

```text
EC 678
EC678
```

were normalized to:

```text
EC678
```

This prevents the same product from appearing as separate products in reports.

## Sales Stage Standardization

Sales stage values were standardized to maintain consistent CRM pipeline analysis.

For example:

```text
qualified
Qualified
```

were standardized to:

```text
Qualified
```

This ensures that pipeline stages are correctly grouped in PivotTables and dashboard calculations.

## Missing Values

Missing values were identified during the Power Query transformation process.

Fields such as customer name, email and phone may contain missing values in the raw dataset.

These values were not replaced with invented information.

Instead, data quality was assessed and missing information was retained where appropriate.

## Duplicate Records

The raw dataset contained 3 intentional duplicate customer records.

Duplicate customer records were identified using `Customer_ID`.

The duplicate records were removed from the cleaned `Customers` table so that each customer appears only once.

As a result:

```text
Raw Customer Records:       153
Unique Customer Records:    150
Duplicate Records Removed:    3
```

The raw data was preserved separately to maintain traceability between the source data and the cleaned CRM data.

## Data Quality Status

A `Data_Quality_Status` field was created in the `Customers` table.

This field provides an indication of whether a customer record passed the defined data-quality checks.

It helps distinguish clean records from records that require attention.

## Lead Data Preparation

The `Leads` table was created from the raw customer data and prepared separately for CRM analysis.

The transformation included:

* Creating a unique `Lead_ID`
* Standardizing text values
* Converting `Lead_Date` to a date type
* Matching products to `Product_ID`
* Standardizing sales stages
* Creating lead scores
* Creating estimated lead values
* Creating next follow-up dates
* Assigning marketing campaign IDs

## Lead Scoring

A lead score was created based on the current sales stage.

The scoring logic was:

| Sales Stage           | Lead Score |
| --------------------- | ---------: |
| New Lead              |         10 |
| Contacted             |         20 |
| Qualified             |         40 |
| Information Pack Sent |         50 |
| Site Survey           |         65 |
| Proposal              |         75 |
| Negotiation           |         85 |
| Won                   |        100 |
| Lost                  |          0 |

This provides a simple way to assess lead progression through the sales pipeline.

## Estimated Lead Value

An estimated value was assigned to leads according to their sales stage.

This provides a consistent demonstration value for pipeline analysis and dashboard reporting.

The resulting values were:

| Sales Stage           | Estimated Value |
| --------------------- | --------------: |
| New Lead              |          £4,000 |
| Contacted             |          £5,000 |
| Qualified             |          £7,000 |
| Information Pack Sent |          £6,000 |
| Site Survey           |          £8,000 |
| Proposal              |          £9,000 |
| Negotiation           |         £10,000 |
| Won                   |         £12,000 |
| Lost                  |              £0 |

## Follow-Up Dates

A `Next_Follow_Up` field was created for leads.

The follow-up date was calculated as seven days after the lead date.

This supports CRM follow-up planning and activity management.

## Campaign Mapping

Leads were connected to marketing campaigns using `Campaign_ID`.

The mapping was based on the lead source.

This allows the dashboard to analyse lead generation and campaign performance.

## Final Data Model Preparation

After cleaning and transformation, the data was loaded into the following CRM tables:

* Customers
* Leads
* Products
* Activities
* Opportunities
* Marketing_Campaigns

These tables were then connected through Power Pivot relationships and used for PivotTables, DAX measures and the interactive CRM dashboard.

## Data Quality Outcome

The cleaning process improved consistency and prepared the dataset for reliable CRM analysis.

The final customer dataset contains:

* 150 unique customers
* 150 unique leads
* Standardized countries
* Standardized product names
* Standardized sales stages
* Cleaned text fields
* Identified missing values
* Removed duplicate customer records
* Consistent data types
* CRM relationships prepared for analysis

## Tools Used

* Microsoft Excel
* Power Query
* Power Pivot
* DAX
* PivotTables
* Data Modelling

```
```
