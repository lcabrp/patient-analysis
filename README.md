# Healthcare Analytics: Patient Readmission Analysis

## Project Overview
This project analyzes patient readmission rates and treatment effectiveness across multiple hospitals. It identifies factors that contribute to patient readmissions and provides insights that could help healthcare providers improve patient outcomes and reduce unnecessary readmissions.

## Dataset Source Note

This course project keeps its original local setup flow so the notebook remains reproducible as submitted. The maintained reusable version of the synthetic patient/hospital generator now lives in the sibling `generating-datasets` repository as `healthcare_readmissions.py`.

## Project Setup Instructions

### Prerequisites
- Python 3.8 or higher
- Git

### Installation Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/lcabrp/patient_analysis_01.git
   cd patient_analysis_01
   ```

2. Create and activate a virtual environment:
   ```bash
   # On Windows
   python -m venv venv
   venv\Scripts\activate

   # On macOS/Linux (Method 1 - Preferred)
   python3 -m venv venv
   source venv/bin/activate

   # On macOS/Linux (Method 2 - If Method 1 fails)
   python3 -m venv venv --without-pip
   source venv/bin/activate
   python3 -m ensurepip --upgrade
   ```

3. Install required dependencies:
   ```bash
   # On Windows
   pip install -r requirements.txt

   # On macOS/Linux
   pip3 install -r requirements.txt
   ```

4. **IMPORTANT**: Run the setup script to generate datasets and initialize the database:
   ```bash
   # On Windows
   python setup_project.py

   # On macOS/Linux
   python3 setup_project.py
   ```

   **This step is mandatory** - it creates the synthetic datasets that the analysis notebook requires.

5. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

6. Open the `healthcare_analysis.ipynb` notebook to view the analysis.

## Execution Order

**⚠️ IMPORTANT: Follow this exact order:**

1. **First**: Run `python3 setup_project.py`
   - Generates synthetic patient and hospital datasets
   - Saves raw data to `./data/` directory as CSV files

2. **Second**: Open and run `healthcare_analysis.ipynb`
   - Loads the pre-generated datasets
   - Performs feature engineering (creates new columns)
   - Creates SQLite database with the enhanced data
   - Demonstrates SQL queries and statistical insights

**Do NOT skip step 1** - the notebook expects the data files to exist and will show an error if they're missing.

### What to Expect

**After running `setup_project.py`:**
- ✅ Synthetic patient and hospital datasets in the `./data/` directory
- ✅ Raw CSV files ready for analysis

**The analysis notebook will then:**
- 📊 Load and explore the pre-generated datasets
- 🧹 Perform data cleaning and validation
- 🔧 Create new features through feature engineering
- 🗄️ Create SQLite database and demonstrate SQL joins
- 📈 Generate three different types of visualizations
- 📋 Provide statistical analysis and business insights

## Technologies Used
- **Python**: Core programming language for data analysis
- **Pandas**: Used for data cleaning, manipulation, and analysis of patient records
- **SQLite**: Database for storing and querying patient and hospital data
- **Matplotlib/Seaborn**: Created visualizations to identify patterns in readmission rates
- **Jupyter Notebooks**: Provides an interactive environment to present code, visualizations, and analysis

## Data Sources
This project uses two synthetic datasets:
1. **Patient Records**: 3,500 records containing patient demographics, diagnoses, treatments, and readmission information
2. **Hospital Information**: 20 records with details about hospitals, including size, location, and specialties

The datasets are designed to simulate real-world healthcare data patterns while ensuring privacy and compliance. The data uses a fixed random seed (42) to ensure reproducible results across different runs. The data dictionary for each dataset is provided in the notebook.

## Project Structure
```
healthcare-analytics/
├── README.md                    # Project documentation
├── requirements.txt             # Python dependencies
├── setup_project.py            # Setup script to initialize project
├── healthcare_analysis.ipynb   # Main analysis notebook
├── healthcare_database.db      # SQLite database (created after setup)
├── data/                       # Generated datasets
│   ├── patient_data.csv        # Patient records dataset
│   └── hospital_data.csv       # Hospital information dataset
└── src/                        # Source code modules
    ├── __init__.py             # Package initialization
    ├── data_generator.py       # Synthetic data generation
    ├── db_utils.py             # Database utilities
    └── visualization.py        # Plotting functions
```

## Key Features Demonstrated
- **Data Generation**: Creates realistic synthetic healthcare datasets
- **Data Cleaning**: Handles missing values and data type conversions
- **Feature Engineering**: Creates new variables for enhanced analysis
- **Database Integration**: Uses SQLite with proper table relationships
- **SQL Queries**: Complex joins and aggregations for data analysis
- **Visualizations**: Three different chart types with consistent styling
- **Statistical Analysis**: Correlation analysis and risk factor identification
- **Documentation**: Comprehensive comments and markdown explanations

## Troubleshooting

### Virtual Environment Issues
If you encounter issues creating the virtual environment:

1. **Error with `python3 -m venv venv`**:
   ```bash
   # Try without pip first
   python3 -m venv venv --without-pip
   source venv/bin/activate
   python3 -m ensurepip --upgrade
   ```

2. **Alternative: Use system Python** (not recommended for production):
   ```bash
   # Skip virtual environment and install directly
   pip3 install -r requirements.txt
   python3 setup_project.py
   ```

3. **Missing Python packages**:
   ```bash
   # On Ubuntu/Debian
   sudo apt-get update
   sudo apt-get install python3-venv python3-pip

   # On CentOS/RHEL
   sudo yum install python3-venv python3-pip
   ```

### Common Issues
- **ModuleNotFoundError**: Make sure you've activated the virtual environment and installed requirements
- **Permission errors**: Try using `pip3 install --user -r requirements.txt`
- **Jupyter not found**: Install with `pip3 install jupyter notebook`
