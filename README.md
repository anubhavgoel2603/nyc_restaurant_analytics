# NYC Restaurant Data Engineering Pipeline
Building a Scalable Data Pipeline for  NYC’s Restaurant Analytics

## 📌 Project Overview
New York City’s restaurant industry is deeply influenced by demographic trends, health regulations, and business dynamics. However, raw datasets are often scattered, unstructured, and challenging to integrate for meaningful analysis. This project builds an end-to-end data pipeline to process, transform, and integrate data from the NYC Population dataset and the DOHMH NYC Restaurant Inspection Results dataset. The pipeline enables downstream analytics, dashboards, and predictive models.

---
## 📊 1. Data Understanding and Ingestion

### **Data Sources**
- **NYC Population by Community Districts Dataset**: Contains borough-wise population statistics.
- **DOHMH NYC Restaurant Inspection Results Dataset**: Contains health inspection data for restaurants, including violations and scores.
- **APIs**: Data is ingested from external sources via APIs and stored in **Azure Data Lake Storage (ADLS)**.

### **Data Ingestion Process**
1. **Extract**: Fetch data from APIs.
2. **Load**: Store raw data in **Azure Data Lake Storage (ADLS)**.
3. **Store**: Data is persisted in a **Bronze table** in Databricks.

---
## ⚙️ 2. ETL and Preprocessing

### **Bronze Layer (Raw Data Storage)**
- Stores unprocessed raw data as ingested from APIs.
- Maintains historical data for auditing and reprocessing.

### **Silver Layer (Data Cleaning and Transformation)**
- Cleans and standardizes the data.
- Removes duplicates, fills missing values, and corrects data types.
- Joins related datasets (restaurant inspections, violations, and population data).

### **Gold Layer (Aggregated & Processed Data)**
- Builds analytical views required for downstream consumption.
- Aggregates insights like:
  - **Cuisine type vs. violations trends**
  - **Best locations for opening restaurants based on population and competition**

---
## 🏗️ 3. Solution Architecture for Each Goal

### **Data Transformations and Aggregations**
| Layer  | Purpose |
|--------|---------|
| **Bronze** | Stores raw ingested data from APIs |
| **Silver** | Cleans, transforms, and integrates datasets |
| **Gold** | Provides final aggregated views for analytics |

### **Output Data Structures**
- **Aggregated restaurant inspection data**
- **Cuisine type trends with violations**
- **Restaurant density vs. population insights**

---
## ☁️ 4. Justification for Utilizing Azure Services

### **Storage**
- **Azure Data Lake Storage (ADLS)**: Used for staging raw and processed data.
- **Delta Lake**: Used for versioning, ACID transactions, and efficient querying.

### **Compute**
- **Databricks**: Used for data transformations and pipeline orchestration.
- **Azure Workflows**: Orchestrates the execution of notebooks (Bronze → Silver → Gold).

---
## 🚀 5. Future Improvements
- **Implement real-time streaming ingestion** for continuous data updates.
- **Enhance predictive modeling** using ML for restaurant location recommendations.
- **Optimize performance** by using **Z-ordering** and **Bloom filters** for large-scale queries.

---
## 🛠️ How to Run the Pipeline
### **Prerequisites**
- Azure Databricks Workspace
- Access to Azure Data Lake Storage (ADLS)
- Configured Databricks Workflows

### **Execution Steps**
1. **Run the Bronze Notebook** to ingest raw data.
2. **Run the Silver Notebook** to clean and transform the data.
3. **Run the Gold Notebook** to generate aggregated insights.
4. **Verify data in Delta Tables** within Databricks.
5. **Use Databricks SQL** to analyze trends and generate reports.

---
### 🔗 References
- [NYC Open Data - Restaurant Inspections](https://data.cityofnewyork.us/Health/DOHMH-New-York-City-Restaurant-Inspection-Results/43nn-pn8j)
- [NYC Open Data - Population](https://data.cityofnewyork.us/City-Government/Population-By-Borough-Community-District/xyye-rtrs)
