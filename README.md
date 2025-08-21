# PySpark Account Balance Report - Q3 2025 Data Dev Tryout

[![PySpark](https://img.shields.io/badge/PySpark-4.0.0-orange)](https://spark.apache.org/)
[![Python](https://img.shields.io/badge/Python-3.11+-blue)](https://python.org/)
[![Java](https://img.shields.io/badge/Java-11+-red)](https://openjdk.java.net/)

**(c) 2025 uCloudify s.r.o** - Hiring Tryout Task Q3 2025

A comprehensive PySpark-based solution for generating account balance reports with opening balances, monthly progressions, and year-to-date calculations for 2025.

## 🎯 Project Overview

This project implements a sophisticated account balance reporting system that generates comprehensive financial reports with:
- **Account-level details**: Account number and customer information
- **Opening balance 2025**: Calculated from historical transactions or explicit opening balance entries
- **Monthly balance progression**: End-of-month balances from January through December 2025
- **Year-to-date summaries**: Total transaction amounts for 2025

## 📊 Key Features

### ✅ Functional Requirements
- **Complete monthly reporting**: Balance end of each month (Jan-Dec 2025)
- **Opening balance calculation**: Robust logic handling both historical transactions and explicit opening balance entries
- **YTD transaction summaries**: Sum of all 2025 transactions per account
- **European CSV support**: Handles semicolon separators and comma decimal notation

### 🏗️ Design Choices & Architecture
- **Modular ETL pipeline**: Reusable `generate_financial_report()` function
- **EffectiveDate strategy**: Unified logic treating opening balances as 2024-12-31 transactions
- **Window functions**: Efficient monthly running totals using PySpark SQL
- **Broadcast joins**: Optimized performance for small reference datasets

### ⚡ Performance Optimizations
- **Memory caching**: `StorageLevel.MEMORY_AND_DISK` for frequently accessed DataFrames
- **Adaptive query execution**: Spark SQL adaptive optimizations enabled
- **Kryo serialization**: Enhanced serialization performance
- **Efficient filtering**: Early data filtering to reduce processing overhead

### 📝 Code Quality & Conventions
- **PEP 8 compliance**: Black formatter integration for consistent code style
- **Comprehensive documentation**: Clear markdown sections and inline comments
- **Configuration constants**: Parameterized values for maintainability
- **Professional structure**: Organized notebook with logical section divisions

### 🧪 Validation & Testing (Bonus Features)
- **Input validation**: Malformed data detection and reporting
- **Comprehensive unit tests**: 4 edge case scenarios with automated assertions
- **Edge case handling**: Mid-year account openings, data corruption, historical accounts
- **Output validation**: Professional formatting with thousands separators

## 🚀 Quick Start

### Prerequisites
- **Python 3.11+**
- **Java 11+** (for PySpark)
- **VS Code** with Jupyter extension (recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Tryout-Data-Dev-2025Q3-PySpark
   ```

2. **Create virtual environment**
   ```bash
   python -m venv pyspark_env_final
   pyspark_env_final\Scripts\activate  # Windows
   # or
   source pyspark_env_final/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set environment variables** (if needed)
   ```bash
   set JAVA_HOME=C:\Program Files\Java\jdk-11.0.x
   ```

### Running the Report

1. **Open the notebook**
   ```bash
   jupyter lab report_pyspark.ipynb
   # or open in VS Code
   ```

2. **Execute cells sequentially**
   - Start with configuration and environment setup
   - Run data loading and preparation sections
   - Execute business logic implementation
   - Review final results and unit tests

## 📁 Project Structure

```
Tryout-Data-Dev-2025Q3-PySpark/
├── README.md                    # This comprehensive documentation
├── requirements.txt             # Python dependencies
├── report_pyspark.ipynb        # Main PySpark implementation
├── Data/                       # Data sources
│   ├── AccountEntries.csv      # Transaction data (European format)
│   ├── AccountInformation.csv  # Account master data
└── .vscode/                    # VS Code configuration
```

## 🔧 Technical Implementation

### Data Processing Pipeline

1. **Data Loading & Validation**
   - European CSV format handling (semicolon separators, comma decimals)
   - Schema inference and type casting
   - Malformed data detection and reporting

2. **Business Logic Implementation**
   - EffectiveDate assignment for universal transaction handling
   - Opening balance calculation with historical transaction support
   - Monthly running totals using Window functions
   - Mid-year account opening logic with sophisticated edge case handling

3. **Output Generation**
   - Professional formatting with Pandas integration
   - Thousands separators and decimal precision
   - NULL handling for mid-year accounts

### Advanced Features

- **Refined Mid-Year Logic**: Accounts with 2025 opening balance entries ignore OpeningDate constraints
- **Data Quality Checks**: Automatic detection and exclusion of malformed amounts
- **Memory Optimization**: Strategic DataFrame caching for performance
- **Error Recovery**: Graceful handling of data quality issues

## 🧪 Unit Testing

The solution includes comprehensive unit tests covering:

- **Historical Harry**: Account with only historical transactions (no opening balance entry)
- **Corrupt Carla**: Data validation with malformed amount handling
- **Mid-year Mike**: Account opened mid-year (NULL balances before opening)
- **Josh**: Account with 2025 opening balance ignoring date constraints

All tests include automated assertions validating calculation accuracy.

## 📈 Assessment Criteria Fulfillment

| Criteria | Implementation |
|----------|---------------|
| **Functional Requirements** | Complete monthly reporting with accurate calculations |
| **Design Choices** | Modular functions, EffectiveDate strategy, Window functions |
| **Performance** | Memory caching, adaptive execution, broadcast joins |
| **Code Quality** | Black formatting, PEP 8, clear documentation |
| **Validation & Testing** | Input validation, comprehensive unit tests, edge cases |

## 🛠️ Development Environment

- **PySpark 4.0.0**: Latest Spark framework
- **Python 3.11**: Modern Python with performance improvements
- **Java 11**: OpenJDK LTS for Spark compatibility
- **Black Formatter**: Automatic code formatting
- **VS Code**: Enhanced development experience

## 📝 Output Sample

The final report generates a professionally formatted table with financial data:

### Sample Report Output

| Account | Customer | Opening Balance 2025 | Jan Balance | ... | Dec Balance | YTD Transactions |
|---------|----------|---------------------|-------------|-----|-------------|------------------|
| 1000001 | John     | 3,322,909.90        | 3,346,333.30 | ... | 3,621,837.36| 298,927.46       |
| 1000002 | Betty    | 38,383,992.40       | 38,383,680.00 | ... | 38,389,768.80| 5,776.40        |
| 1000003 | Jessica  | 5,584,843.90        | 5,596,967.23 | ... | 5,588,998.43| 4,154.53        |
| 1000004 | Josh     | 988,786.90          | 986,432.60  | ... | 1,459,465.30| 470,678.40      |

### Key Features in Output:
- **Thousands separators**: All amounts formatted with commas (1,234.56)
- **Consistent precision**: Two decimal places for all financial values
- **NULL handling**: Empty cells for accounts opened mid-year (before opening month)
- **Complete monthly progression**: All 12 months from January to December 2025
- **Professional formatting**: Clean, readable table structure suitable for business reporting

## 🚀 Future Enhancements

- **Multi-Currency Support**: Implement currency conversion with real-time exchange rates from external APIs
- **Dynamic Currency Display**: Allow users to view balances in different base currencies (EUR, USD, GBP)
- **Historical Exchange Rates**: Track currency fluctuations over time for accurate historical reporting
- **Currency-Specific Formatting**: Localized number formatting based on account's primary currency

---

**Author**: Juraj  
**Contact**: [GitHub Profile](https://github.com/Juraj131)  
**Project**: uCloudify Data Dev Tryout Q3 2025

