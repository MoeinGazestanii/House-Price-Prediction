# House-Price-Prediction
Bengaluru House Price Prediction
This project is a machine learning pipeline capable of predicting house prices in Bengaluru, India. It analyzes a dataset of real estate transactions, cleans and processes the data, detects outliers, and utilizes machine learning algorithms to estimate property prices based on features like location, square footage, bathrooms, and BHK (bedrooms, hall, kitchen).

📌 Project Overview
The goal of this project is to build a model that provides accurate price estimates for home buyers and sellers. The notebook covers the entire end-to-end process from data loading to model selection using GridSearchCV.

🛠️ Technologies Used
Python

Pandas (Data manipulation and cleaning)

NumPy (Numerical operations)

Matplotlib & Seaborn (Data visualization)

Scikit-Learn (Machine learning and metric evaluation)

📂 Dataset
The project uses the bengaluruhousedata.csv file containing the following key features:

location: The neighborhood in Bengaluru.

size: The BHK count (e.g., "2 BHK", "4 Bedroom").

total_sqft: The total area of the property.

bath: Number of bathrooms.

price: Price of the property (target variable).

Note: Columns such as area_type, society, balcony, and availability were dropped during preprocessing as they were determined to be less significant for this specific modeling approach.

⚙️ Key Steps in the Notebook
1. Data Cleaning
Handling Missing Values: Null values in critical columns like location and size are dropped.

Standardizing size: Converted the size column (e.g., "2 BHK") into a numerical bedroom feature.

Processing total_sqft: The dataset contained ranges (e.g., "1133 - 1384") and non-standard entries (e.g., "Sq. Meter"). A custom function sqft_to_num converts ranges to their average and filters out unstructured data.

2. Feature Engineering
Price Per Sqft: A new feature price_per_sqft is created to assist with outlier detection.

Dimensionality Reduction: Locations with fewer than 10 data points are grouped into a single category called "other". This reduces the number of dummy variables required (One Hot Encoding) and improves model efficiency.

3. Outlier Detection & Removal
The project implements logic to remove data errors and extreme anomalies:

Business Logic: Removed records where the square footage per bedroom is significantly low (threshold: 300 sqft per bedroom).

Statistical Outliers: Using mean and standard deviation per location to filter out extreme price_per_sqft values.

Bedroom/Price Logic: Removed 2 BHK apartments that are significantly more expensive than 3 BHK apartments in the same area with similar square footage.
