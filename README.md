# 📊 Data Cleaning Project

A comprehensive data cleaning pipeline for processing and standardizing job-related datasets using Python and pandas.

## 🎯 Project Overview

This project provides a systematic approach to cleaning and preprocessing job-related data, transforming raw CSV data into a clean, analysis-ready format. The pipeline handles common data quality issues including missing values, inconsistent formatting, and data type conversions.

## 📁 Project Structure

```
data-cleaning-project/
├── dataset/
│   ├── data.csv           # Raw input dataset
│   └── CleanedData.csv    # Processed output dataset
├── main.ipynb             # Main cleaning script
├── requirements.txt       # Has the required packages            
└── README.md              # This file
```

## 🔧 Features

### Data Standardization
- **Column Name Normalization**: Converts column names to lowercase, removes spaces, and standardizes formatting
- **Data Type Consistency**: Ensures proper data types across all columns

### Data Quality Improvements
- **Missing Value Handling**: Strategic imputation for numerical columns using mean values
- **Invalid Data Replacement**: Converts placeholder values (-1) to appropriate representations
- **Text Standardization**: Consistent formatting for categorical variables

### Advanced Data Processing
- **Location Parsing**: Splits location strings into separate city and code columns
- **Salary Range Processing**: Converts salary ranges (e.g., "$44k-$99k") into minimum, maximum, and average salary columns
- **Boolean Standardization**: Normalizes boolean-like columns to consistent TRUE/FALSE format

## 🛠️ Requirements

```python
pandas>=2.0.0
numpy>=1.24.0
seaborn>=0.12.0
matplotlib>=3.7.0
```

## 🚀 Usage

1. **Prepare your data**: Place your raw CSV file in the `dataset/` directory as `data.csv`

2. **Run the cleaning .ipynb script**: 
   ```bash
   # (Cell by Cell execution)
   main.ipynb
   ```

3. **Output**: The cleaned dataset will be saved as `dataset/CleanedData.csv`

## 📋 Data Transformations

| Step | Transformation | Description |
|## 🔍 Example Transformations

Based on the actual dataset, here are the key transformations:

### Before Cleaning:
```
Age: [44, 66, "", 64, 25] → Missing values represented as empty strings
Location: ["India,In", "New York,Ny", "India In", "Australia Aus"] → Inconsistent formatting
Rating: [5.4, 3.5, -1, 4.4] → -1 used as placeholder
Salary: ["$44k-$99k", "$55k-$66k", "$77k-$89k"] → Range format
Easy Apply: [TRUE, TRUE, -1, -1] → Mixed boolean representation
```
<img width="1421" height="227" alt="uncleaned data" src="https://github.com/user-attachments/assets/2522d73a-61f5-4687-9ada-c50eeb70d2e2" />


### After Cleaning:
```
age: [44.0, 66.0, 37.8, 64.0, 25.0] → Missing filled with mean (37.8)
location_city: ["India", "New York", "India", "Australia"] → Standardized
city_code: ["In", "Ny", "In", "Aus"] → Separated codes
rating: [5.4, 3.5, 4.2, 4.4] → -1 replaced with mean (4.2)
min_salary: [44000, 55000, 77000] → Extracted minimum values
max_salary: [99000, 66000, 89000] → Extracted maximum values
avg_salary: [71500, 60500, 83000] → Calculated averages
easy_apply: ["TRUE", "TRUE", "TRUE", "TRUE"] → Standardized to TRUE
```
<img width="1422" height="230" alt="cleaned data" src="https://github.com/user-attachments/assets/612fce59-7b15-4d3b-9208-6529e4016533" />



## 📊 Input Data Format

The script processes a CSV file with the following columns:
- `Index`: Row identifier (0-28, 29 records total)
- `Age`: Numerical age values (13-66, contains missing values represented as empty cells)
- `Salary`: Salary ranges in format "$XXk-$YYk" (e.g., "$44k-$99k", "$10k-$49k")
- `Rating`: Company/job ratings 0-7.8 (contains -1 placeholders and missing values)
- `Location`: Location strings with inconsistent formatting:
  - Proper format: "India,In", "New York,Ny"
  - Inconsistent format: "India In", "Australia Aus"
- `Established`: Year established 1932-2020 (contains -1 placeholders for unknown)
- `Easy Apply`: Boolean values (TRUE, -1 as placeholder for missing)

## 🎯 Output Features

The cleaned dataset includes:
- **Standardized column names** (lowercase, underscore-separated)
- **Clean numerical data** with appropriate missing value handling
- **Parsed location data** (separate city and country code columns)
- **Structured salary information** (min, max, and average salary columns)
- **Consistent boolean formatting**

## 📈 Quality Assurance

The pipeline includes built-in quality checks:
- ✅ Data shape validation
- ✅ Missing value reporting
- ✅ Summary statistics generation
- ✅ Data type verification


## 📝 Notes

- The script handles missing values strategically based on data type
- All transformations preserve data integrity while improving consistency
- The pipeline is designed to be robust against common data quality issues
- Output includes comprehensive summary statistics for validation

## 🔍 Data Quality Issues Addressed

Based on the actual dataset analysis, this pipeline specifically handles:

### Missing Values
- **Age column**: 6 missing values out of 29 records (20.7%)
- **Rating column**: 1 completely missing value, plus -1 placeholders

### Inconsistent Data Formats
- **Location formatting**: Mixed formats ("India,In" vs "India In", "Australia Aus")
- **Boolean representation**: Mixed TRUE and -1 values in Easy Apply column
- **Placeholder values**: -1 used inconsistently across multiple columns

### Data Range Validation
- **Age range**: 13-66 years (youngest: 13, oldest: 66)
- **Rating scale**: 0-7.8 (with some 0 ratings that may need investigation)
- **Establishment years**: 1932-2020 (87-year span)
- **Salary ranges**: $10k-$101k (wide compensation range)

### Geographic Distribution
- **India**: 10+ records
- **New York**: 10+ records  
- **Australia**: 6+ records

---
