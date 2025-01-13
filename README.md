# Housing Prices Estimator

## Overview & Purpose
I built a regression model that estimates house listing prices and a program (`Recommender.ipynb`) that outputs a range of "reasonable" prices for a given house. Sellers can use this range to reassess whether their price is reasonable. Buyers and sellers can use it as a basis for negotiation purposes (lower end for buyers, higher end for sellers).

While this type of regression project is a common theme across data science projects, I'd like to make mine useful by narrowing my project's scope to houses located in a South Tangerang, a city in Indonesia. This narrow scope, although restricting the audience, gives more value to those who do find use of it. I chose this city specifically since I own property and lived in this city before - I believe I have a reasonable sense of judgment that I believe will help me with validity-checks of the dataset's and model's numbers. 

## Dataset
The dataset `HousingData.csv`, scraped by Gerry Zani from from the online housing marketplace "Rumah.com" (Cited below). This dataset includes house listings from South Tangerang, Indonesia. Variables include:
1. `url`
2. `location`
3. `area` (land size of the house)
4. `bed` (number of bedrooms)
5. `bath` (number of bathrooms)
6. `price` (in Indonesian Rupiah, IDR)
7. `price per area` (discarded as it is derived from `price` and `area`)


## Usage
If you would like to use this project, do the following:
1. Open `Recommender.ipynb`
2. Run the program
3. Input data related to your house listing, as requested by the program.
4. Your recommended range for pricing will be outputted.

## Process
### 1. Data Cleaning & Preprocessing
- Removed duplicates and standardized formats.
- Identified and removed extreme outliers (e.g., houses priced at less than one cent).

### 2. Feature Engineering & Selection
- Visualized common words in `location` and `url` using word clouds.
- Created dummy variables for these columns via OneHotEncoding.
- Used a correlation heatmap to filter out likely-insignificant (R² < 0.01) and highly cross-correlated dummy variables.

### 3. Model Development
- Selected a random forest model, which is suitable for this dataset since it has many binary variables (dummy variables). Since decision trees/random forests make use of if-statements, I think this regression technique would "structurally" be suitable.
- Evaluated the dummy variables' impact - they achieved a 37% reduction in the regression model's Mean Absolute Error (MAE).

### 4. Price Recommendation Program
- Built `Recommender.ipynb`, which accepts new house data and outputs a pricing range based on the model and its MAE.

## Personal Evaluation of Model
This dataset only provided us with 7 variables (one of which is not suitable for use), so with this limitation, I think the MAE achieved was fairly pleasing to see. However, I believe there is still room to keep decreasing the MAE, and so for this I'd like to come back to this project with more regression techniques (e.g XGBoost), which I may implement depending on how it performs.

## Citation
Dataset scraped by Gerry Zani from Rumah.com. Posted on Kaggle for public use - https://www.kaggle.com/datasets/gerryzani/housing-price-in-south-tangerang-city-indonesia/data.
