# 🦷 Healthcare Data Cleaning, Modelling & Dashboard Analysis

## 📌 Project Overview

This project involved cleaning, transforming, modelling, and analysing a healthcare provider dataset obtained from Kaggle.

I started by cleaning and preparing the raw healthcare data using Microsoft Excel Power Query. The dataset contained provider information, age groups, delivery systems, provider types, user counts, service counts, previous user counts, and supporting annotation fields.

After cleaning the data, I structured it into fact and dimension tables and worked with Power Pivot to understand data modelling and one-to-many relationships.

I later continued the project by using the prepared dataset to build a dashboard for analysing healthcare service utilisation and provider performance.

This project represents my practical learning journey from raw data preparation to data modelling and dashboard development.

---

## 🎯 Project Objective

The main objectives of this project were to:

- Clean and transform the raw healthcare dataset.
- Standardise inconsistent text and values.
- Handle missing and blank records appropriately.
- Check data quality using Power Query profiling tools.
- Prepare the dataset for analysis and modelling.
- Separate measurable records from descriptive information.
- Create fact and dimension tables.
- Understand and apply one-to-many relationships.
- Analyse healthcare service utilisation and provider performance.
- Develop a dashboard that communicates important findings clearly.

---

## 🗂️ Dataset

**Source:** Kaggle

**Dataset Type:** Healthcare Provider Data

The dataset contained information relating to healthcare providers, service utilisation, users, age groups, delivery systems, and provider classifications.

### Key Variables

- `RENDERING_NPI` — Provider identifier
- `PROVIDER_LEGAL_NAME` — Provider name
- `CALENDAR_YEAR` — Year
- `DELIVERY_SYSTEM` — Delivery system
- `PROVIDER_TYPE` — Provider classification
- `AGE_GROUP` — Age category
- `ADV_USER_CNT` — User count
- `ADV_SVC_CNT` — Service count
- `PREV_USER_CNT` — Previous user count
- Annotation fields — Supporting measure information

An important characteristic of the dataset was that the same provider could appear multiple times because providers could have records for different age groups.

Therefore, repeated provider IDs were not automatically treated as errors.

---

## 🛠️ Tools & Techniques

### Tools

- Microsoft Excel
- Power Query
- Power Pivot
- DAX
- Data Modelling

### Techniques

- Data Cleaning
- Data Transformation
- Data Profiling
- Data Type Management
- Text Cleaning
- Missing Value Handling
- Duplicate Investigation
- Fact Table Creation
- Dimension Table Creation
- One-to-Many Relationships
- Data Modelling
- Dashboard Development
- KPI Development
- Data Visualization

---

## 🔄 Project Workflow

Raw Healthcare Dataset  
↓  
Power Query Import  
↓  
Data Cleaning & Transformation  
↓  
Data Quality Checks  
↓  
Fact & Dimension Tables  
↓  
Power Pivot Data Model  
↓  
Data Analysis  
↓  
Dashboard Development  
↓  
Insights & Findings

---

## 🧹 Data Preparation

I began the project by importing the raw healthcare dataset into Power Query.

### 1. Promoted Headers

I promoted the appropriate row so that the actual field names became the column headers.

### 2. Changed Data Types

I reviewed the data types and assigned appropriate types to the columns.

- Text fields were treated as text.
- Year was treated as a number.
- User counts were treated as numerical fields.
- Service counts were treated as numerical fields.

### 3. Removed Blank Rows

I checked for unnecessary blank records and removed them so that empty rows would not be treated as healthcare records.

### 4. Handled Missing Values

I investigated missing descriptive values and used Fill Down or Fill Up where appropriate when the blanks were caused by the structure of the source data.

### 5. Cleaned Provider Names

Provider names contained inconsistent formatting and unnecessary spaces.

I used:

- Trim
- Capitalize Each Word

to improve consistency in provider names.

### 6. Checked Data Quality

I used Power Query's Column Quality and Column Profile features to examine:

- Valid values
- Error values
- Empty values

This helped me verify the quality of the transformed dataset.

---

## 🧩 Fact & Dimension Tables

After cleaning the data, I separated detailed healthcare records from descriptive information.

### Fact Healthcare

The Fact Healthcare table retained the detailed healthcare records and measurable information such as:

- Advanced user counts
- Advanced service counts
- Previous user counts
- Provider information
- Age group
- Year
- Delivery system

The fact table represents **what happened**.

### Dimension Tables

I created supporting dimension tables, including:

- Dim Provider
- Dim Age

Dimension tables provide descriptive information used to categorise, filter, and provide context for the records in the fact table.

---

## 📊 Data Modelling

I used Power Pivot to create relationships between the fact and dimension tables.

The model followed a one-to-many relationship structure:

**Dim Age → Fact Healthcare**

**Dim Provider → Fact Healthcare**

The dimension tables represent the "one" side, while the Fact Healthcare table represents the "many" side.

---

## ⚠️ Challenges & Problem Solving

### 1. Duplicate Provider IDs

One of the major challenges occurred when I attempted to create a relationship in Power Pivot.

The relationship could not be created because the column being used on the dimension side contained duplicate values.

Initially, repeated provider IDs looked like duplicates that should be removed.

However, after investigating the source data, I discovered that the same provider could legitimately appear for different age groups.

For example:

| Provider | Age Group |
|---|---|
| 1003003781 | AGE 0-20 |
| 1003003781 | AGE 21+ |

This taught me that repeated values are not automatically errors.

The correct approach was to investigate what each record represented before removing anything.

### 2. Dimension Table Uniqueness

I learned that a dimension table needs a unique key on the "one" side of a one-to-many relationship.

The Fact Healthcare table can contain repeated foreign-key values because the same provider or category can occur across multiple records.

I therefore restructured the dimension tables around unique values.

### 3. Dim Age Contained Only Two Rows

When I removed duplicates from the Age Group field, I was left with:

- AGE 0-20
- AGE 21+

At first, I thought data had been removed incorrectly.

After checking the original dataset, I confirmed that these were the only unique age categories available.

Therefore, the reduced dimension table was correct.

### 4. Close & Load Issue

I also encountered an issue where Close & Load To did not behave as expected for one of the dimension queries.

This helped me understand that Power Query queries do not always need to be loaded directly into an Excel worksheet.

Depending on the purpose of the query, it can instead be loaded into the Data Model.

### 5. Provider Text Formatting

Provider information contained inconsistent formatting and unnecessary spaces.

I solved this using Power Query transformations such as:

- Trim
- Capitalize Each Word

---

## 📈 Dashboard Development

After completing the cleaning and modelling stages, I continued the project by developing a dashboard to analyse healthcare service utilisation and provider performance.

The dashboard was designed to provide a high-level view of:

- Total services
- Total providers
- Total users
- Services per user
- Preventive services
- Service distribution
- Provider performance
- Age-group service volume
- Service categories

### Dashboard Visuals

The dashboard included:

#### 1. Services by Delivery System

A donut chart showing the distribution of healthcare services across delivery systems.

#### 2. Services by Age Group & Category

A bar chart comparing service volumes across age groups and service categories such as:

- Treatment
- Preventive
- Exam

#### 3. Provider Performance Leaderboard

A table comparing providers using measures such as:

- Users
- Total Services
- Services per User

#### 4. Age Group Volume Distribution

A column chart comparing service volume across the available age groups.

#### 5. Top 10 Providers by Total Services

A bar chart highlighting the providers with the highest total service counts.

#### 6. Dental Care Pipeline

A funnel visual showing the distribution of services across major service categories.

---

## 📊 Key Performance Indicators

The dashboard included the following KPIs:

| KPI | Value |
|---|---:|
| Total Services | 62M |
| Total Providers | 11K |
| Total Users | 10M |
| Services per User | 6.38 |
| Preventive Services | 14M |

These KPIs provide a quick overview of healthcare service utilisation and provider activity.

---

## 💡 Key Findings

### 1. Treatment Services Represented the Largest Service Category

Treatment services accounted for the largest volume within the service-category analysis, followed by preventive services and examinations.

### 2. Fee-for-Service Was the Dominant Delivery System

The delivery-system analysis showed that Fee-for-Service represented the majority of recorded services, accounting for approximately 85% of the displayed service distribution.

### 3. Younger Age Group Had Higher Service Volume

The age-group analysis showed that the AGE 0-20 group recorded a higher service volume than the AGE 21+ group in the dashboard.

### 4. Provider Performance Varied Considerably

The provider analysis showed differences in the number of users served, total services recorded, and services per user.

The top-performing providers therefore did not necessarily have the same performance profile across every measure.

### 5. Some Providers Had High Services per User

The provider leaderboard highlighted providers with particularly high services-per-user values, showing that service volume alone does not provide the complete picture of provider utilisation.

---

## 📷 Dashboard Preview

### Healthcare Services & Utilization Dashboard

_Add dashboard screenshot here._

<!-- Example:
![Healthcare Services & Utilization Dashboard](dashboard-image.png)
-->

---

## 🧠 What I Learned

This project strengthened my practical understanding of the complete data preparation and modelling process.

### Technical Skills

- How to import and clean data using Power Query.
- How to use data profiling to identify quality issues.
- How to handle missing values appropriately.
- How to standardise text fields.
- How to manage data types.
- How to distinguish legitimate repeated records from actual data problems.
- How fact tables and dimension tables work.
- Why dimension keys need to be unique.
- How one-to-many relationships work.
- How Power Pivot supports data modelling.
- How data modelling affects dashboard development.
- How to create and interpret dashboard KPIs and visualisations.

### Problem-Solving Skills

One of my biggest lessons from this project was that I should not automatically delete repeated values.

Instead, I learned to ask:

> What does each row represent?

Understanding the meaning of the data helped me distinguish between legitimate repeated records and actual modelling problems.

---

## 🚀 Project Outcome

I transformed a raw healthcare provider dataset into a cleaner and more structured dataset suitable for analysis and data modelling.

The project progressed from:

**Data Cleaning → Data Transformation → Data Profiling → Fact & Dimension Tables → Data Modelling → Dashboard Development → Insights**

This project gave me practical experience working with a real-world style dataset and strengthened my understanding of how data preparation and modelling support business intelligence and dashboard development.

---
