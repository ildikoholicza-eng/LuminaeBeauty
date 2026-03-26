# LumineaBeauty: Omni-Channel Marketing Intelligence Platform
### *A Medallion Architecture Portfolio Project*

## 🌟 Project Overview
**LumineaBeauty** is an end-to-end data warehousing solution built using **Microsoft SQL Server (T-SQL)**. This project transforms messy, synthetic e-commerce data into a "Single Source of Truth" for business intelligence. 

I initiated this project to test my technical grit by applying a **Medallion Architecture** to a complex marketing setting. Drawing on my **HND in Marketing** and my background in the beauty industry, I designed this system to reconcile advertising spend with transactional revenue—a core challenge in modern e-commerce.

This project was inspired by the architectural principles taught by **Baraa Khatib**, which I then adapted and expanded upon independently to handle high-complexity marketing datasets.

## 🏗️ The Architecture
I implemented a three-layer Medallion system to ensure data integrity and scalability:
* **Bronze (Raw):** The landing zone for original CSV files. Data is stored as `VARCHAR(MAX)` to ensure 100% ingestion success without data type conflicts.
* **Silver (Cleaned):** Data is cast to correct types (Dates, Decimals, Integers), duplicates are removed, and `NULL` values are handled (imputed as 'unknown' or 0).
* **Gold (Curated):** Business-level aggregates and joined tables optimized for reporting and visualization.

## 📊 Data Sources (Synthetic)
The warehouse ingests and synchronizes five core marketing and sales streams:
1.  **Orders Raw:** Customer transactions and revenue.
2.  **Web Analytics Raw:** Site traffic and user behavior.
3.  **Email Analytics Raw:** Newsletter performance (Opens, Clicks).
4.  **Google PPC Raw:** Search engine marketing spend and performance.
5.  **Meta Ads Raw:** Social Media advertising metrics.

## 🧠 Key Technical Features & Challenges

### **1. Resilience Against "Dirty" Data**
The dataset was intentionally AI-generated to be "hard and messy," simulating real-world tracking issues. I encountered significant challenges with missing campaign tags and null values. This project pushed me to my limits, but I remained resilient, learning new ways to script SQL and troubleshoot deep logic errors.

### **2. Strategic Data Quality Gate**
During the transition to the Gold Layer (Star Schema), I identified that the volume of invalid data prevented a meaningful ROAS (Return on Ad Spend) calculation. Since I lacked access to the source generator to "fix" the upstream logic, I made a strategic decision:
* **Decision:** I implemented a strict **Data Quality Gate**, excluding records with `NULL` or `Unknown` campaign names.
* **Result:** This allowed for a technically sound Star Schema that provides a "Clean Source of Truth" for stakeholders, prioritizing accuracy over volume.

### **3. Advanced T-SQL Scripting**
* **Idempotent Scripts:** Used `IF NOT EXISTS` and `DROP` logic to ensure the environment is safely repeatable.
* **Deterministic Hashing:** Implemented **MD5 Hashing** to join disparate datasets (Marketing vs. Orders) where no natural primary key existed.
* **Defensive Design:** Used dynamic SQL (`EXEC`) for schema creation to bypass batch requirements.

## 🛠️ How to Use
1.  **Clone the Repo:** Download the SQL scripts and CSV files.
2.  **Run Setup:** Execute `0_setup_database.sql` to create the `LumineaBeauty` database and the Bronze/Silver/Gold schemas.
3.  **Ingest Data:** Use the provided scripts to import the CSV files into the Bronze schema.
4.  **Transform:** Run the Silver and Gold layer scripts to process the data into the final reporting views.

## 🛣️ Roadmap
**Database Design** ➔ **Bronze Ingestion** ➔ **Silver Cleaning** ➔ **Gold Aggregation** ➔ **Dashboard Integration (Power BI/Tableau)**

---
*Note: This project represents my commitment to striving for senior-level standards. It proves that I have the resilience to tackle projects "bigger than I can chew" and the technical ability to deliver a professional finish.*
