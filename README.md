# 📊 Financial Metrics & Cohort Analysis Platform

A production-grade data analytics platform showcasing advanced SQL, Python ETL, and business intelligence skills. Perfect for Data Analyst portfolios.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13%2B-green) ![License](https://img.shields.io/badge/License-MIT-orange)

---

## 🎯 Project Goals

- ✅ Build an **end-to-end ETL pipeline** (Extract → Transform → Load)
- ✅ Demonstrate **advanced SQL** (window functions, CTEs, complex joins)
- ✅ Perform **cohort analysis** and customer segmentation
- ✅ Calculate key **financial metrics** (RFM, LTV, CAC, Churn Risk)
- ✅ Create **interactive Power BI dashboards** for business insights
- ✅ Showcase **production-quality code** with logging and error handling

---

## 📦 What's Included

```
financial-analytics-platform/
├── etl_pipeline.py           # Main ETL pipeline (ready to run!)
├── config.py                 # Configuration & database settings
├── schema.sql                # Database schema creation script
├── requirements.txt          # Python dependencies
├── .env.example              # Environment variables template
├── Project_1_Guide.md        # Complete project specification
└── README.md                 # This file
```

---

## 🚀 Quick Start (15 minutes)

### Step 1: Clone & Setup
```bash
# Clone the repository
git clone <your-repo-url>
cd financial-analytics-platform

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Step 2: Setup PostgreSQL Database
```bash
# 1. Install PostgreSQL (if not already installed)
# 2. Create a new database
psql -U postgres
CREATE DATABASE financial_analytics;
\q

# 3. Run the schema script
psql -U postgres -d financial_analytics -f schema.sql

# If prompted for password, enter your PostgreSQL password
```

### Step 3: Configure Environment
```bash
# Copy the example environment file
cp .env.example .env

# Edit .env with your database credentials
# DB_USER=postgres
# DB_PASSWORD=your_password
# DB_NAME=financial_analytics
```

### Step 4: Prepare Data
```bash
# Download a sample dataset from Kaggle:
# - Brazilian E-commerce Dataset: 
#   https://www.kaggle.com/datasets/olistbrazil/brazilian-ecommerce
# - Or Online Retail Dataset:
#   https://www.kaggle.com/datasets/mashregb/online-retail-data-analysis

# Extract and place CSV files in data/raw/:
# - customers.csv
# - products.csv
# - transactions.csv
```

### Step 5: Run ETL Pipeline
```bash
# Create logs directory
mkdir logs

# Run the pipeline
python etl_pipeline.py

# Expected output:
# ✓ Extracted X customer records
# ✓ Extracted Y product records
# ✓ Extracted Z transaction records
# ✓ Customer data transformed: A records
# ...
# ✓ ETL PIPELINE COMPLETED SUCCESSFULLY!
```

---

## 📊 Running Analytics Queries

Once data is loaded, run these SQL queries in your database:

### Query 1: RFM Segmentation
```sql
-- See which customers are Champions, Loyal, etc.
SELECT * FROM calculate_rfm() LIMIT 20;
```

### Query 2: Cohort Analysis
```sql
-- Track customer retention by cohort month
SELECT * FROM cohort_base LIMIT 50;
```

### Query 3: Churn Risk Scoring
```sql
-- Identify customers at risk of churning
SELECT * FROM calculate_churn_risk() WHERE risk_category = 'High Risk' LIMIT 20;
```

### Query 4: Monthly Summary
```sql
-- View monthly business metrics
SELECT * FROM monthly_summary ORDER BY month DESC;
```

---

## 🔑 Key Metrics Calculated

| Metric | Definition | Business Use |
|--------|-----------|--------------|
| **Recency** | Days since last purchase | How recently is customer engaged? |
| **Frequency** | Total transactions | How often do they buy? |
| **Monetary** | Total amount spent | How much value do they bring? |
| **Cohort Retention** | % of cohort returning each month | Is retention improving? |
| **RFM Score** | R + F + M (each 1-5) | Which customers are most valuable? |
| **Churn Risk** | Probability of churning (0-100) | Who might leave? |
| **Lifetime Value** | Total spent (simplified LTV) | Long-term customer value |
| **Average Order Value** | Revenue / # orders | What's typical purchase size? |

---

## 🏗️ Architecture

```
CSV Files (Raw Data)
        ↓
    EXTRACT (Read CSV)
        ↓
    TRANSFORM (Clean, normalize)
        ↓
    VALIDATE (Quality checks)
        ↓
    LOAD (Insert to PostgreSQL)
        ↓
PostgreSQL Tables
        ↓
    SQL QUERIES (Analytics)
        ↓
Power BI Dashboard
```

---

## 💾 Database Schema

### Core Tables
- **customers**: Customer master data
- **products**: Product catalog
- **transactions**: Order facts (fact table)

### Analytical Tables
- **customer_metrics**: Aggregated RFM and churn scores
- **monthly_summary**: Month-level KPIs

### Views & Functions
- `cohort_base`: Base view for cohort analysis
- `calculate_rfm()`: RFM segmentation function
- `calculate_churn_risk()`: Churn risk scoring function

---

## 🧪 Testing & Validation

The ETL pipeline includes built-in validation:

```
✓ Check for null values in critical fields
✓ Validate data types and formats
✓ Remove duplicates
✓ Verify date ranges
✓ Check for invalid amounts/quantities
```

View validation logs in `logs/etl_pipeline.log`

---

## 📈 Power BI Dashboards (Next Steps)

Once data is loaded, create these dashboards in Power BI:

1. **Executive Dashboard**
   - KPI cards: Revenue, Customers, AOV, Retention Rate
   - Revenue trend over time
   - Customer acquisition vs churn

2. **Cohort Performance Dashboard**
   - Cohort retention heatmap
   - Retention trends by cohort age
   - Cohort quality metrics

3. **Customer Segmentation Dashboard**
   - RFM segment distribution
   - Segment performance metrics
   - Segment trends

4. **Churn Risk Dashboard**
   - Risk distribution (High/Medium/Low)
   - At-risk customer list
   - Risk factors

---

## 📝 Configuration Reference

Edit `config.py` to customize:

```python
# Database settings
DB_HOST = 'localhost'
DB_PORT = 5432
DB_NAME = 'financial_analytics'

# Data paths
DATA_RAW_PATH = 'data/raw'
DATA_PROCESSED_PATH = 'data/processed'

# ETL options
BATCH_SIZE = 10000
MAX_NULL_PERCENTAGE = 0.05

# Churn definition
CHURN_DAYS_THRESHOLD = 180
```

---

## 🐛 Troubleshooting

### Issue: "connection refused"
```bash
# Check if PostgreSQL is running
# Mac: brew services list
# Windows: Services app > PostgreSQL
# Linux: sudo systemctl status postgresql
```

### Issue: "database does not exist"
```bash
# Create the database
psql -U postgres
CREATE DATABASE financial_analytics;
```

### Issue: "permission denied for schema public"
```bash
# Grant permissions
psql -U postgres -d financial_analytics
GRANT ALL ON SCHEMA public TO YOUR_USER;
```

### Issue: "CSV file not found"
```bash
# Make sure CSV files are in data/raw/
# Expected files: customers.csv, products.csv, transactions.csv
ls data/raw/
```

---

## 📚 Files Explained

| File | Purpose |
|------|---------|
| `etl_pipeline.py` | Main ETL orchestration with classes for extract, transform, validate, load |
| `config.py` | Centralized configuration (DB credentials, paths, thresholds) |
| `schema.sql` | DDL to create all tables, indexes, views, functions |
| `.env` | Environment variables (created from .env.example) |
| `requirements.txt` | Python package dependencies |

---

## 🚀 GitHub Optimization Tips

For maximum GitHub impact:

✅ **Good commit messages:**
```
git commit -m "feat: add cohort retention analysis queries"
git commit -m "refactor: improve ETL pipeline error handling"
git commit -m "docs: add RFM segmentation explanation"
```

✅ **Add .gitignore:**
```
*.csv
.env
logs/
__pycache__/
*.pyc
.DS_Store
```

✅ **Create professional README with:**
- Architecture diagram ✓
- Quick start guide ✓
- Project structure ✓
- Usage examples ✓
- Database schema docs ✓

✅ **Add badges:**
```markdown
![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13%2B-green)
```

---

## 📊 Sample Output

After running successfully, you should see:

```
============================================================
Financial Analytics ETL Pipeline Initialized
Data Path: data/raw
Database: localhost
============================================================

============================================================
EXTRACT PHASE - Loading all data sources
============================================================
✓ Extracted 5000 customer records
✓ Extracted 500 product records
✓ Extracted 50000 transaction records

============================================================
TRANSFORM PHASE - Cleaning and normalizing data
============================================================
✓ Customer data transformed: 4950 records
✓ Product data transformed: 495 records
✓ Transaction data transformed: 49500 records

============================================================
VALIDATION PHASE - Quality checks
============================================================
✓ No nulls in customer_id
✓ No duplicate customer_ids
✓ All prices > 0
...
✓ Customer validation PASSED
✓ Product validation PASSED
✓ Transaction validation PASSED

============================================================
LOAD PHASE - Inserting into database
============================================================
✓ Loaded 4950 customer records
✓ Loaded 495 product records
✓ Loaded 49500 transaction records

============================================================
✓ ETL PIPELINE COMPLETED SUCCESSFULLY!
Total duration: 45.32 seconds
============================================================
```

---

## 🎓 Learning Resources

- **Window Functions in SQL**: https://www.postgresql.org/docs/current/functions-window.html
- **Cohort Analysis Guide**: https://www.amplitude.com/blog/cohort-analysis
- **RFM Segmentation**: https://www.customerlifecyclemarketinginstitute.com/RFM.html
- **Power BI Tutorials**: https://learn.microsoft.com/en-us/power-bi/

---

## 🤝 Contributing

This is your portfolio project! Extend it:
- Add more advanced SQL queries
- Create predictive churn models
- Build real-time dashboards
- Add unit tests
- Deploy to cloud (AWS/GCP)

---

## 📄 License

MIT License - feel free to use this as a template for your portfolio

---

## 💡 Next Steps

1. ✅ Complete the basic setup (this checklist)
2. ✅ Run the ETL pipeline
3. ⬜ Create Power BI dashboards
4. ⬜ Add advanced analysis notebooks
5. ⬜ Deploy to GitHub with professional documentation
6. ⬜ Add to your portfolio with live demo link

---

## 📞 Support

For issues or questions:
1. Check troubleshooting section above
2. Review project guide: `Project_1_Guide.md`
3. Check PostgreSQL logs
4. Review ETL logs: `logs/etl_pipeline.log`

---

**Made for Data Analyst Portfolio | Showcasing SQL, Python, and Analytics Skills** 🚀

Last updated: June 2025
