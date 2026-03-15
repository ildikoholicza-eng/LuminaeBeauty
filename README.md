# LuminaeBeauty
## Project Overview 
#### This project demonstrates the design and implementation of a professional Data warehouse using Microsoft SQL Server(T-SQL). It follows the Medallion Architecture to transform raw, synthetic e-commerce data into actionable business intelligence. The goal is to provide a clean, reliable " Single Source of Truth" for the company moving from messy ingestion to high-value reporting.

### The Architecture
#### I have implemented a three-layer Medallion system to ensure data integrity and scalability:
#### - Bronze (Raw): Landing zone for original CSV files. Data is stored as VARCHAR(MAX) to prevent ingestion failures.
#### - Silver (Cleaned): Data is cast to correct types (Dates, Decimals, Integers), duplicates are removed, and NULLs are handled.
#### - Gold (Curated): Business-Level aggregates and joined tables optimised for reporting and visualisation.

### Data Sources (Synthetic) 
#### The warehouse ingests five core marketing and sales streams:
#### 1, Orders Raw: Customer transactions and revenue.
#### 2, Web Analytics Raw: Site traffic and user behaviour.
#### 3, Email Analytics Raw: Newsletter performance  (Open, Clicks).
#### 4, Google PPC Raw: Search engine marketing spend and performance.
#### 5, Meta Ads Raw: Social Media advertising metrics. 
### Key Technical Features

#### Indempotent Scripts: All SQL scripts use IF NOT EXISTS and DROP TABLE IF EXISTS logic. This ensures the environment can be reset or redeployed safely without causing  system errors or accidental data loss.
#### Defensive Schema Design: Schemas are created dynamically using EXEC to bypass batch requirements, demonstrating advanced T-SQL scripting.
#### Future-Ready: The Gold Layer is designed specifically to connect to visualisation tools  like PowerBI or Tableau for executive reporting. 

### How to Use 
#### 1,  Clone the repo: Download the SQL scripts and CSV files.
#### 2, Rum Setup: Execute  0_setup_database.sql to create the LuminaeBeauty database and the Bronze/Silver/Gold schemas.
#### 3, Ingest Data: Use the provided scripts to import the CSV files into the Bronze schema.
#### 4, Transform: Run the Silver and Gold layer scripts to process the data.




##### Roadmap: Database Schema Design -> Bronze Ingestion Script -> Silver Layer Data Cleaning -> Gold Layer Aggregations -> Dashboard Integration 



