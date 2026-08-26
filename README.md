# TravelTriangle Travel Package Market Analysis

## 📌 Project Overview

This project analyzes travel package listings scraped from
**TravelTriangle** to understand destination popularity, pricing
patterns, package value, discount strategies, and the factors associated
with package prices.

The project combines **web scraping, data cleaning, exploratory data
analysis (EDA), feature engineering, visualization, and statistical
hypothesis testing** to convert raw travel-package listings into
actionable business insights.

------------------------------------------------------------------------

## 🎯 Business Problem

TravelTriangle offers travel packages that vary by destination, trip
duration, price, hotel rating, discounts, and cities covered. Customers
need an effective way to compare packages based on cost and value, while
travel businesses need to understand destination demand and the factors
that influence package pricing.

### Business Objectives

-   Identify destinations with the highest package availability.
-   Identify premium and relatively affordable destinations.
-   Compare destinations based on price per day to evaluate value for
    money.
-   Determine whether trip duration is associated with package price.
-   Determine whether hotel rating affects package price.
-   Identify destinations offering higher average discounts.
-   Identify packages with greater absolute price savings.
-   Understand how package characteristics influence pricing.
-   Validate important relationships using statistical tests.

------------------------------------------------------------------------

## 📊 Dataset

The dataset was collected from TravelTriangle's India travel-package
listing pages.

### Scraping Details

-   **Source:** TravelTriangle India tour packages
-   **Pages scraped:** 60
-   **Packages collected:** 880
-   **Raw columns:** 9
-   **Scraping tools:** Python, Requests, BeautifulSoup
-   **Output dataset:** `travel_packages.csv`

### Raw Features

  Column           Description
  ---------------- ----------------------------------------
  Package Name     Name of the travel package
  Destination      Primary destination of the package
  Days             Number of travel days
  Nights           Number of nights
  Current Price    Current package price
  Old Price        Original/listed price before discount
  Discount         Discount percentage
  Hotel Rating     Hotel category included in the package
  Cities Covered   Cities included in the itinerary

------------------------------------------------------------------------

## 🛠️ Technologies Used

-   Python
-   Pandas
-   NumPy
-   Requests
-   BeautifulSoup
-   Regular Expressions
-   Matplotlib
-   Seaborn
-   SciPy
-   Jupyter Notebook

------------------------------------------------------------------------

## 🔄 Project Workflow

``` text
TravelTriangle Website
        ↓
Web Scraping
        ↓
Raw Travel Package Dataset
        ↓
Data Understanding
        ↓
Data Cleaning
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
Visualization
        ↓
Statistical Testing
        ↓
Business Insights
        ↓
Recommendations
```

------------------------------------------------------------------------

## 🧹 Data Cleaning

The following preprocessing steps were performed:

-   Checked dataset shape and data types.
-   Checked missing values.
-   Handled missing values using median imputation where appropriate.
-   Checked duplicate records.
-   Standardized text fields such as destination and package
    information.
-   Checked numerical variables for unusual values and outliers.
-   Retained genuine variation in prices, discounts, and trip durations
    rather than removing valid business observations.

### Data Quality

-   **880 records** after scraping.
-   **No duplicate records** were identified.
-   Missing values in `Old Price`, `Discount`, and `Hotel Rating` were
    handled.
-   The cleaned dataset was used for downstream analysis.

------------------------------------------------------------------------

## ⚙️ Feature Engineering

Additional features were created to support business analysis:

### Price Difference

``` python
df["Price Difference"] = df["Old Price"] - df["Current Price"]
```

Measures the absolute monetary saving associated with a package.

### Price Per Day

``` python
df["Price Per Day"] = df["Current Price"] / df["Days"]
```

Used to compare package value while accounting for different trip
durations.

### Number of Cities

The number of destinations/cities covered by each itinerary was derived
from `Cities Covered`.

### Price Category

Packages were categorized into price segments to support categorical
analysis.

### Trip Length

Trip-duration categories were created to compare shorter and longer
itineraries.

------------------------------------------------------------------------

## 📈 Exploratory Data Analysis

The EDA was structured around business questions rather than only
producing charts.

### 1. Which destinations have the highest package availability?

Used destination frequency analysis to identify destinations with the
largest number of listed packages.

### 2. Which destinations are the most expensive?

Compared average and median package prices across destinations.

### 3. Which destinations provide the best value for money?

Compared destinations using average `Price Per Day`.

### 4. Does trip duration affect package price?

Analyzed the relationship between `Days` and `Current Price` using
correlation and visualization.

### 5. Does hotel rating affect package price?

Compared package prices across hotel-rating groups using group-based
analysis and ANOVA.

### 6. Which destinations offer the highest discounts?

Compared average discount percentages across destinations.

### Visualizations

The project uses appropriate visualizations including:

-   Bar charts
-   Histograms
-   Box plots
-   Scatter plots
-   Count plots
-   Correlation heatmaps
-   Group-based comparison charts

------------------------------------------------------------------------

## 🧪 Statistical Analysis

Statistical testing was used to validate important EDA findings.

### Pearson Correlation

**Question:** Is trip duration associated with package price?

-   Correlation coefficient: **r ≈ 0.61**
-   p-value: **\< 0.001**

Result: There is a statistically significant positive relationship
between trip duration and package price.

### One-Way ANOVA

**Question:** Does package price differ across hotel ratings?

-   F-statistic: **16.70**
-   p-value: **\< 0.001**

Result: Package prices differ significantly across hotel-rating groups.

### Independent T-Test

**Question:** Is there a significant difference between selected
hotel-rating price groups?

-   t-statistic: **-2.30**
-   p-value: **0.023**

Result: The tested hotel-rating groups show a statistically significant
difference in average package price.

### Chi-Square Test

**Question:** Is hotel rating associated with package price category?

-   Chi-square statistic: **16.96**
-   p-value: **0.009**

Result: There is a statistically significant association between hotel
rating and price category.

------------------------------------------------------------------------

## 💡 Key Business Insights

### Destination Availability

**Munnar, Gangtok, and Goa** have the strongest package availability,
indicating substantial representation in the TravelTriangle package
portfolio.

### Premium Destinations

**Gangtok, Dalhousie, and Darjeeling** show the highest average package
prices among the analyzed destinations.

### Value for Money

**Jaisalmer, Kovalam, and Udaipur** provide comparatively attractive
price-per-day values.

### Trip Duration

Trip duration has a meaningful positive relationship with package price.
The correlation of approximately **0.61** is statistically significant,
indicating that longer itineraries tend to cost more.

### Hotel Rating

Hotel rating is a statistically significant pricing factor. Higher-rated
hotel packages, particularly **5-star packages**, command substantially
higher average prices.

### Discounts

**Calangute and Jaipur** show comparatively high average discounts,
making them relevant destinations for price-sensitive customers and
promotional strategies.

------------------------------------------------------------------------

## 💼 Business Recommendations

### For TravelTriangle

1.  **Use destination-specific pricing strategies** rather than applying
    a uniform pricing approach.
2.  **Segment packages by hotel rating and trip duration** because these
    factors are significantly associated with price.
3.  **Promote high-value destinations** using price-per-day metrics
    instead of total package price alone.
4.  **Use targeted discounts** in destinations where promotional pricing
    is already effective.
5.  **Create differentiated premium packages** for destinations and
    hotel categories that support higher prices.
6.  **Use package-level savings in marketing** to highlight the monetary
    benefit of discounted packages.
7.  **Monitor highly represented destinations** such as Munnar, Gangtok,
    and Goa for market saturation and competitive positioning.

### For Customers

-   Compare packages using **price per day**, not only total price.
-   Consider hotel rating when evaluating premium packages.
-   Look for destinations with attractive discounts and lower daily
    costs.
-   Compare itinerary length and cities covered before choosing the
    cheapest package.

------------------------------------------------------------------------

## 📁 Recommended GitHub Repository Structure

``` text
TravelTriangle-Travel-Package-Analysis/
│
├── web_scraping_EDA_project.ipynb
├── travel_packages.csv
├── EDA_project_presentation.pptx
├── README.md
└── requirements.txt
```

### Optional

You can also add:

``` text
├── images/
│   └── charts/
└── data/
    └── travel_packages.csv
```

------------------------------------------------------------------------

## ▶️ How to Run the Project

### 1. Clone the repository

``` bash
git clone <your-github-repository-url>
cd TravelTriangle-Travel-Package-Analysis
```

### 2. Install dependencies

``` bash
pip install pandas numpy requests beautifulsoup4 lxml matplotlib seaborn scipy jupyter
```

### 3. Launch Jupyter Notebook

``` bash
jupyter notebook
```

Open:

``` text
web_scraping_EDA_project.ipynb
```

------------------------------------------------------------------------

## ⚠️ Disclaimer

This project was created for **educational and analytical purposes**
using publicly accessible travel-package listing information.

Travel package prices, discounts, availability, and website structures
can change over time. Therefore, the results represent the dataset
collected during the scraping period and should not be treated as
real-time pricing information.

------------------------------------------------------------------------

## 👨‍💻 Author

**Sakshith**

### Project

**Travel Package Market Analysis --- Web Scraping & Exploratory Data
Analysis of TravelTriangle.com**

------------------------------------------------------------------------

## ⭐ Project Highlights

-   60 web pages scraped
-   880 travel packages analyzed
-   9 raw features
-   Feature engineering and data cleaning
-   Destination-level pricing analysis
-   Value-for-money analysis
-   Discount analysis
-   Hotel-rating analysis
-   Pearson correlation
-   ANOVA
-   Independent t-test
-   Chi-square test
-   Business recommendations
