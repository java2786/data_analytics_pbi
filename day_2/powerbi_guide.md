# Power BI Guide: ETL with Indian Data

## Session Overview 
**Focus**: Extract, Transform, Load (ETL) processes using Indian datasets
**Target**: Students with Power BI Desktop installed
**Emphasis**: 70% on Transform, 20% on Extract, 10% on Basic Visualization

---

## Part 1: Introduction & Setup 

### What is ETL in Power BI?
- **Extract**: Getting data from various sources (CSV, Excel, JSON, databases)
- **Transform**: Cleaning, shaping, and preparing data for analysis
- **Load**: Bringing the transformed data into Power BI for visualization

### Today's Learning Path
1. Extract data from multiple Indian datasets
2. Deep dive into ***Power Query Editor*** for transformations
3. Create basic visualizations with clean data

---

## Part 2: Data Extraction 

### Sample Indian Datasets to Use

#### Dataset 1: Indian States Population (CSV)
Create a CSV file with this data:
```
State,Population_2021,Area_sq_km,Capital,Region
Uttar Pradesh,199812341,240928,Lucknow,North
Maharashtra,112374333,307713,Mumbai,West
Bihar,104099452,94163,Patna,East
West Bengal,91276115,88752,Kolkata,East
Madhya Pradesh,72626809,308245,Bhopal,Central
Tamil Nadu,72147030,130060,Chennai,South
Rajasthan,68548437,342239,Jaipur,North
Karnataka,61095297,191791,Bengaluru,South
Gujarat,60439692,196024,Gandhinagar,West
Andhra Pradesh,49386799,162968,Amaravati,South
```

#### Dataset 2: Indian Cricket Team Performance (Excel)
Create an Excel file with sheets:
**Sheet 1 - Match Results**
```
Year,Matches_Played,Won,Lost,Draw,Win_Percentage
2019,45,28,12,5,62.2
2020,32,19,8,5,59.4
2021,38,24,10,4,63.2
2022,42,29,9,4,69.0
2023,40,27,8,5,67.5
```

**Sheet 2 - Player Stats**
```
Player_Name,Matches,Runs,Average,Strike_Rate
Virat Kohli,150,8500,56.7,92.3
Rohit Sharma,140,7800,55.7,88.9
KL Rahul,85,3200,37.6,86.4
Rishabh Pant,78,2800,35.9,126.8
```

#### Dataset 3: Indian IT Companies Revenue (JSON)
Create a JSON file:
```json
{
  "companies": [
    {"name": "Tata Consultancy Services", "revenue_cr": 191754, "employees": 528748, "founded": 1968, "headquarters": "Mumbai"},
    {"name": "Infosys", "revenue_cr": 147171, "employees": 314015, "founded": 1981, "headquarters": "Bengaluru"},
    {"name": "Wipro", "revenue_cr": 86015, "employees": 250000, "founded": 1945, "headquarters": "Bengaluru"},
    {"name": "HCL Technologies", "revenue_cr": 78829, "employees": 210000, "founded": 1976, "headquarters": "Noida"},
    {"name": "Tech Mahindra", "revenue_cr": 57000, "employees": 157000, "founded": 1986, "headquarters": "Pune"}
  ]
}
```

### Extraction Process in Power BI

1. **Open Power BI Desktop**
2. **Get Data Options**:
   - Home tab → Get Data → Text/CSV (for population data)
   - Get Data → Excel (for cricket data)
   - Get Data → JSON (for IT companies)

3. **Loading Process**:
   - Preview the data
   - Click "Transform Data" (not "Load") to open Power Query Editor

---

## Part 3: Data Transformation Deep Dive 

### Working with CSV Data (Indian States Population)

#### Initial Data Issues to Address:
- Check data types
- Handle missing values
- Create calculated columns
- Split and merge columns

#### Transformation Steps:

**Step 1: Data Type Corrections**
- Select Population_2021 column → Data Type → Whole Number
- Select Area_sq_km column → Data Type → Whole Number
- Verify text columns are set to Text type

**Step 2: Create Calculated Columns**
- Add Column tab → Custom Column
- Column Name: "Population_Density"
- Formula: `[Population_2021] / [Area_sq_km]`

**Step 3: Create Population Categories**
- Add Column → Conditional Column
- Column Name: "Population_Category"
- Logic:
  - If Population_2021 > 100000000 then "Very High"
  - Else if Population_2021 > 50000000 then "High"
  - Else "Medium"

**Step 4: Split Region into Sub-categories** (Example exercise)
- Add custom column for detailed regions
- Use Replace Values for data cleaning

### Working with Excel Data (Cricket Performance)

#### Multi-Sheet Handling:
1. **Navigate between sheets** in Power Query
2. **Combine data** from multiple sheets if needed
3. **Create relationships** between tables

#### Transformation Exercises:

**For Match Results Sheet:**
- Calculate "Total_Results" = Won + Lost + Draw
- Create "Performance_Rating" based on Win_Percentage
- Format Win_Percentage as percentage

**For Player Stats Sheet:**
- Filter players with Average > 40
- Create "Performance_Category" based on Strike_Rate
- Round Average to 1 decimal place

### Working with JSON Data (IT Companies)

#### JSON Specific Transformations:
1. **Expand the JSON structure**
   - Click expand button on the companies column
   - Select all fields to expand

2. **Data Cleaning**:
   - Rename columns (remove "companies." prefix)
   - Convert revenue_cr to proper number format
   - Create "Company_Age" = 2024 - founded

3. **Advanced Transformations**:
   - Create "Revenue_per_Employee" calculation
   - Categorize companies by size (employees)
   - Group by headquarters city

### Advanced Transform Techniques

#### Text Transformations:
- **Clean text data**: Trim, Clean, Proper Case
- **Extract information**: Split columns by delimiter
- **Replace values**: Standardize city names, company names

#### Number Transformations:
- **Rounding**: Round revenue figures
- **Statistical operations**: Average, median calculations
- **Binning**: Group continuous data into categories

#### Date Transformations (if adding date columns):
- **Extract components**: Year, month, quarter
- **Calculate age/duration**: Years since founding
- **Date formatting**: Consistent date formats

#### Grouping and Aggregation:
- **Group By**: Region-wise population summary
- **Pivot operations**: Transform row data to columns
- **Merge queries**: Combine data from different sources

### Data Quality Checks:
1. **Column profiling**: Check data distribution
2. **Remove duplicates**: Ensure data uniqueness
3. **Handle null values**: Replace or remove
4. **Validate relationships**: Ensure referential integrity

---

## Part 4: Loading and Basic Visualization 

### Loading Transformed Data
1. **Close & Apply** from Power Query Editor
2. **Verify data load** in the Data pane
3. **Check relationships** in Model view

### Quick Visualizations with Indian Data

#### Chart 1: State Population Bar Chart
- Drag State to Axis
- Drag Population_2021 to Values
- Sort by population descending

#### Chart 2: Regional Population Distribution
- Create a Pie Chart
- Region in Legend
- Sum of Population_2021 in Values

#### Chart 3: Cricket Performance Trend
- Line Chart with Year on Axis
- Win_Percentage on Values

#### Chart 4: IT Company Revenue Comparison
- Horizontal Bar Chart
- Company names on Axis
- Revenue on Values

### Dashboard Layout Tips:
- Use consistent colors representing Indian themes
- Add appropriate titles
- Ensure charts are readable
- Use filters for interactivity

---

## Part 5: Best Practices & Wrap-up 

### Transform Best Practices:
1. **Always preview data** before loading
2. **Document transformations** with clear step names
3. **Test with sample data** first
4. **Keep original data intact** - work on copies
5. **Use consistent naming conventions**
6. **Optimize for performance** - remove unnecessary columns early

### Common Indian Data Challenges:
- **Mixed languages**: English and Hindi text
- **Different date formats**: DD/MM/YYYY vs MM/DD/YYYY
- **Currency formatting**: Lakhs and Crores
- **Regional variations**: State name spellings
- **Data encoding**: Special characters in names

### Next Steps for Students:
1. Practice with more complex Indian datasets
2. Learn DAX for advanced calculations
3. Explore Power BI Service for sharing
4. Study data modeling techniques
5. Build industry-specific dashboards (retail, manufacturing, etc.)

---

## Homework Assignment:
Create a Power BI dashboard using any Indian dataset of your choice (education, agriculture, or economic data) and apply at least 5 different transformation techniques learned today.

---

## Additional Resources:
- Practice with open Indian government datasets
- Explore Power Query M language documentation
- Join Power BI community forums
- Follow Indian Power BI user groups and meetups

**Session Complete!** Students should now be comfortable with ETL processes and ready to tackle real-world Indian business data challenges.
