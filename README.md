# Aftermarket Car Analysis 🚗

## Dataset and Files

### 🌐 **Original Dataset Source**
- The original dataset was obtained from [Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data)

### 💾 **Output Files**
- Due to the large size of the output files, they are hosted on Google Drive instead of GitHub.
  
  - **Jupyter Notebook Output File**: [Link to Notebook Output](https://drive.google.com/file/d/1TQHDP2wWIpLqpkqRiQl2hAKR797IMgfk/view?usp=drive_link)
  - **Excel Output File**: [Link to Excel Output](https://drive.google.com/file/d/1MGVJiROIay1-hTaDoPq5_ElJQfUmxL0S/view?usp=drive_link)

### 🔄 **Initial Data Handling Attempt**
- **Pivoted Approach**: Initially attempted to split the dataset for loading into a free data lake like BigQuery, but pivoted to a double cleaning process (Python and MS Excel) due to numerous errors and BigQuery's max local file upload size of 100 MB. The code for splitting the CSV is [here](https://github.com/josephhmltn/Aftermarket_Car_Analysis/blob/main/Splitting_CSV_file.ipynb).

## Summary of Jupyter Notebook Data Cleaning and Transformation

### 📚 **Importing Libraries and Data Load**
- Essential libraries imported for data load and manipulation, Pandas and OS.

### 🧹 **Initial Data Cleaning and Transformation**
- **Clean & Tidy**: Cleaning and transformation operations like:
  - Changing data types
  - Dropping unneccessary columns
  - Removing rows where year and odometer had NaN values
  - Removing rows where price was 0
  - Removing rows where price and odometer were above 350,000 and 250,000 respectively
  - Splitting posting_date column into multiple columns for later use

### 🛠️ **Results**
- **Input**: Original file had 426880 rows across 22 columns.
- **Output**: Results CSV has 382367 rows across 29 columns.

## Summary of Further Data Cleaning in Excel 💻📊

### 🗑️ **Duplicate Removal**
- Loaded the Jupyter notebook output file into MS Excel.
- **Remove Duplicates Feature**: Removed duplicates based on VIN, price, odometer, region, date, and description to address common reposting issues on Craigslist.
- **Manual Review**: Further checked for duplicate VIN numbers using 'Conditional Formatting' and manually removed remaining duplicates.

### 🚗 **Price and Odometer Validation**
- Reviewed price and odometer columns for values under 1000.
- **Price Segmentation**: Segmented prices into bins (0-250, 251-500, 501-750, 751-1000) and removed all listings under $1000 to avoid skewing results.
- **Odometer Filtering**: Removed erroneous odometer readings (0-499) while keeping valid new vehicle listings (500-1000+).

### 🔍 **Description Column Parsing**
- Conducted text parsing on the description column to identify any further duplicates.

### 📉 **Data Reduction**
- Original dataset had 382,367 rows; post-cleaning, the dataset was reduced to 169,034 (+1 for headers).

### 📈 **Summary Statistics Post-Cleaning**
1. **Price Range**: Approximately $1,000 to $350,000 (max price for a Ferrari).
2. **Odometer Range**: 500 to 250,000 miles, with high-mileage vehicles being reliable brands like Honda and Toyota.
3. **Posting Dates**: Cover April and May 2021.
4. **Geographical Spread**: Includes all 50 states plus DC, with California (CA) and Florida (FL) having the highest postings.
5. **Common Vehicle Colors**: White (30,633 postings) and Black (25,443 postings).
6. **Most Common Vehicle Years**: 2013 (12,507 postings), followed closely by 2014, 2015, 2017, and 2018.

## Analysis and Visualizations are a WIP and will be uploaded when complete.
