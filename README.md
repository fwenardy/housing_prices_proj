# Housing Prices Estimator

## Overview & Purpose
I built a regression model that estimates house listing prices and a program (`Recommender.ipynb`) that outputs a range of "reasonable" prices for a given house. Sellers can use this range to reassess whether their price is reasonable. Buyers and sellers can use it as a basis for negotiation purposes (lower end for buyers, higher end for sellers).

## Dataset
The dataset `HousingData.csv`, scraped by Gerry Zani from from the online housing marketplace "Rumah.com". Link: https://www.kaggle.com/datasets/gerryzani/housing-price-in-south-tangerang-city-indonesia/data), which includes house listings from South Tangerang, Indonesia. Variables include:
1. `url`
2. `location`
3. `area` (land size of the house)
4. `bed` (number of bedrooms)
5. `bath` (number of bathrooms)
6. `price` (in Indonesian Rupiah, IDR)
7. `price per area` (discarded as it is derived from `price` and `area`)

## Process

### 1. Data Cleaning & Preprocessing
- Removed duplicates and standardized formats.
- Identified and removed extreme outliers (e.g., houses priced at less than one cent).

### 2. Feature Engineering & Selection
- Visualized common words in `location` and `url` using word clouds.
- Created dummy variables for these columns via OneHotEncoding.
- Used a correlation heatmap to filter out likely-insignificant (R² < 0.01) and highly cross-correlated dummy variables.

### 3. Model Development
- Selected a random forest model, which is suitable for this dataset since it has many binary variables (dummy variables), and thus to me it makes sense that the random forest's decision trees would 
- Evaluated the dummy variables' impact - they achieved a 37% reduction in the regression model's Mean Absolute Error (MAE).

### 4. Price Recommendation Program
- Built `Recommender.ipynb`, which accepts new house data and outputs a pricing range based on the model and its MAE.

## Usage
1. **Prepare Input Data:** Ensure it includes features like location, area, and property details.
2. **Run the Program:** Input data into `Recommender.ipynb` to generate a pricing range.

## Future Work
- Use geospatial analysis for enhanced location feature engineering.
- Add more housing attributes to improve accuracy.
- Explore ensemble learning techniques to further reduce MAE.

## Citation
Dataset scraped by Gerry Zani from [Rumah.com](https://www.kaggle.com/datasets/gerryzani/housing-price-in-south-tangerang-city-indonesia/data).
