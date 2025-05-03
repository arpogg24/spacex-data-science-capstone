# SpaceX Falcon 9 First Stage Landing Prediction

## Data and Notebooks
This project focuses on predictive analysis using real-world data from SpaceX launches to determine whether the Falcon 9 first stage will land successfully. The economic significance is substantial: SpaceX can offer launches at $62 million compared to competitors' $165 million largely due to their reusable first stages. The project comprises seven comprehensive notebooks that progress from data collection through visualization to machine learning model development and interactive dashboard creation.

The data was collected from two sources:
1. The SpaceX API, which provides detailed information about launches, boosters, and landing outcomes
2. Web-scraped data from Wikipedia's "List of Falcon 9 and Falcon Heavy launches" page

A detailed description of each notebook's content and methodology is provided below.

## Project Goals
The primary goal of this analysis was to develop predictive models that can accurately determine whether a SpaceX Falcon 9 first stage will land successfully based on launch parameters. This has practical applications for:
1. Competing aerospace companies estimating SpaceX costs
2. Investors assessing technological maturity in the launch industry
3. Understanding the key factors that influence landing success

## Implementation Process

### Lab 01: Data Collection via API
- **Goal**: Establish a robust dataset foundation by retrieving comprehensive SpaceX launch data
- **Outcome**: Created a clean, filtered DataFrame containing only relevant Falcon 9 launches with complete metadata
- **Technical Skills**: API interaction with requests library, JSON parsing, data cleaning, structured data organization
- **Tools**: Python, requests, pandas, numpy, datetime

### Lab 02: Web Scraping
- **Goal**: Obtain an alternative data source to complement API data and validate information
- **Outcome**: Successfully extracted structured launch data from Wikipedia using automated parsing
- **Technical Skills**: HTML parsing, CSS selector navigation, text extraction and cleaning
- **Tools**: BeautifulSoup, requests, pandas

### Lab 03: Data Wrangling
- **Goal**: Transform raw launch data into a machine learning-ready format with clear classification labels
- **Outcome**: Created binary success/failure labels while gaining initial insights into launch patterns
- **Technical Skills**: Exploratory data analysis, categorical data transformation, classification labeling
- **Tools**: pandas, matplotlib

### Lab 04: SQL Exploratory Data Analysis
- **Goal**: Apply structured querying to extract meaningful patterns and milestones from launch history
- **Outcome**: Uncovered key insights about performance patterns across launch sites, booster versions, and mission parameters
- **Technical Skills**: Database management, SQL query construction, relationship analysis
- **Tools**: SQLite, pandas

### Lab 05: Data Visualization and Feature Engineering
- **Goal**: Identify significant relationships between launch parameters and landing success through visual analysis
- **Outcome**: Revealed critical factors affecting landing success and prepared optimized feature set for modeling
- **Technical Skills**: Statistical visualization, feature transformation, pattern recognition
- **Tools**: Matplotlib, Seaborn, pandas, scikit-learn

### Lab 06: Interactive Dashboard
- **Goal**: Create an accessible tool for stakeholders to explore landing success relationships
- **Outcome**: Developed an interactive web application allowing real-time filtering and visualization of success patterns
- **Technical Skills**: Web application development, callback programming, interactive visualization
- **Tools**: Dash, Plotly, pandas

### Lab 07: Machine Learning Models
- **Goal**: Develop predictive models to determine landing success probability based on launch parameters
- **Outcome**: Created and compared four different prediction models, with logistic regression providing the best performance
- **Technical Skills**: Machine learning algorithm implementation, hyperparameter tuning, model evaluation
- **Tools**: scikit-learn, numpy, pandas, matplotlib

## Key Results
The analysis produced several significant findings:

### Factors Influencing Landing Success
- Launch site significantly impacts success rates (KSC LC-39A and VAFB SLC 4E showing ~77% success)
- As SpaceX gained experience (higher flight numbers), success rates improved
- Orbit type affects landing difficulty, with certain orbits showing consistently lower success rates
- Payload mass has a complex relationship with landing success, varying by launch site and orbit
- Clear temporal improvement in success rates from 2013-2020 as technology matured

### Predictive Modeling
- Logistic regression provided the best performance, suggesting relatively linear relationships
- More complex models (SVM, KNN, Decision Trees) did not significantly improve prediction accuracy
- The final model achieved good accuracy on the test dataset, providing a reliable prediction tool
- Analysis revealed that relatively simple models can effectively predict landing outcomes

## Technical Skills Demonstrated
This project showcases proficiency in numerous data science skills:

- Data collection (API interaction, web scraping)
- Data cleaning and preprocessing
- SQL database analysis
- Statistical analysis and pattern recognition
- Data visualization (static and interactive)
- Feature engineering and selection
- Machine learning model development and evaluation
- Web dashboard creation
- Python programming (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Dash, Plotly)

## Conclusion
This project successfully developed predictive models to determine the likelihood of successful SpaceX Falcon 9 first stage landings. The analysis identified key factors influencing landing success and demonstrated that relatively simple machine learning models can effectively capture these relationships. The interactive dashboard provides stakeholders with an accessible tool to explore these relationships themselves. The insights gained could be valuable for competing aerospace companies, investors, and anyone interested in understanding the technological advancement of reusable rocket technology.

This analysis was completed as part of the IBM Data Science Professional Certificate, but all aspects of the analysis and code are entirely my own.
