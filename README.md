

# 📊 Campaign Data Processing Project

Welcome to the **Campaign Data Processing Project**! This project is designed to clean and transform campaign data, making it ready for insightful analysis. Below, you'll find a step-by-step guide on how the data is processed, details about the dataset, and the problems it aims to solve.

---

## 📁 Project Structure
The project follows a structured approach to processing campaign data, with each step performed in a Jupyter notebook.

### **1️⃣ Convert Day to String**
- **Notebook Cell ID:** `3b83afe6-a565-4856-8162-d6b88e2f2689`
- **Code:**
  ```python
  campaign["day"] = campaign["day"].astype(str)
  ```
- **Description:** Converts the `day` column in the `campaign` DataFrame to a string type. This ensures proper concatenation when creating date fields.

### **2️⃣ Create Last Contact Date**
- **Notebook Cell ID:** `6ae7df34-bed0-4f44-9a8b-fe931c9db9f1`
- **Code:**
  ```python
  campaign["last_contact_date"] = campaign["year"] + "-" + campaign["month"] + "-" + campaign["day"]
  ```
- **Description:** Combines `year`, `month`, and `day` columns to create a `last_contact_date` column. This simplifies date-related analysis.

### **3️⃣ Convert Last Contact Date to Datetime**
- **Notebook Cell ID:** `82dc3035-88c6-4ffa-bdd9-949a35b95ceb`
- **Code:**
  ```python
  campaign["last_contact_date"] = pd.to_datetime(campaign["last_contact_date"],
                                                 format="%Y-%b-%d")
  ```
- **Description:** Converts the `last_contact_date` column to a datetime format for easier date manipulation and analysis.

### **4️⃣ Drop Unnecessary Columns**
- **Notebook Cell ID:** `19cfaaa2-c939-4550-8444-820a38d65c62`
- **Code:**
  ```python
  campaign.drop(columns=["month", "day", "year"], inplace=True)
  ```
- **Description:** Removes `month`, `day`, and `year` columns since they are no longer needed, keeping the dataset clean and optimized.

### **5️⃣ Save DataFrames to CSV**
- **Notebook Cell ID:** `9ff84a0c-5ee6-4cdb-9c70-55a08cbadd33`
- **Code:**
  ```python
  client.to_csv("client.csv", index=False)
  campaign.to_csv("campaign.csv", index=False)
  economics.to_csv("economics.csv", index=False)
  ```
- **Description:** Saves the `client`, `campaign`, and `economics` DataFrames as CSV files for easy sharing and further analysis.

---

## 📊 Data Overview

### **Campaign Data**
- **Columns:** `year`, `month`, `day`, `last_contact_date`, etc.
- **Description:** Contains information about campaign contact dates and relevant details.

### **Client Data**
- **Columns:** Various client-related attributes.
- **Description:** Contains information about clients involved in the campaign.

### **Economics Data**
- **Columns:** Various economic indicators.
- **Description:** Includes economic data that may influence the campaign's performance.

---

## 🛠️ Problems Addressed

✅ **Data Inconsistency:**
- Initially, the dataset had separate columns for `year`, `month`, and `day`, making it difficult to analyze dates. The `last_contact_date` column simplifies the structure.

✅ **Data Type Issues:**
- The `day` column was originally an integer, which could cause issues during concatenation. Converting it to a string ensures smooth processing.

✅ **Redundant Columns:**
- After creating `last_contact_date`, the original `year`, `month`, and `day` columns were unnecessary, so they were removed to keep the dataset clean.

---


## 📋 Requirements

- **Python 3.x**
- **pandas**
- **Jupyter Notebook**


## 🙏 Acknowledgments

A big thank you to the contributors and the open-source community for their valuable resources and support! 🎉

