# Lab 01: SpaceX Falcon 9 First Stage Landing Prediction: Data Collection

This notebook documents my process of collecting and preparing data for predicting whether SpaceX Falcon 9 first stages will land successfully. The economic significance of this prediction stems from SpaceX's ability to offer launches at $62 million compared to competitors' $165 million, largely due to their reusable first stages.

## Key Components and Workflow:

1. **Initial Setup**: I imported essential libraries (requests, pandas, numpy, datetime) and defined helper functions to extract specific data from the SpaceX API.

2. **API Data Collection**: I made requests to the SpaceX API to retrieve launch data, then used helper functions to gather detailed information about:
   - Booster versions
   - Launch sites (names, coordinates)
   - Payload details (mass, orbit type)
   - Core data (landing outcomes, flight numbers, technical specifications)

3. **Data Filtering and Formatting**: 
   - Selected relevant columns for analysis
   - Filtered for single-core launches and single-payload missions
   - Converted dates to proper datetime format
   - Limited the dataset to launches before November 13, 2020

4. **Data Consolidation**: Combined all extracted information into a comprehensive dictionary, then converted it to a pandas DataFrame.

5. **Falcon 9 Isolation**: Created a new DataFrame containing only Falcon 9 launches, removing Falcon 1 data, and reset the flight numbers accordingly.

6. **Missing Value Handling**: Identified missing values in the dataset, particularly in the PayloadMass column, and replaced them with the column mean while preserving intentional None values in the LandingPad column.

7. **Data Export**: Saved the cleaned dataset to a CSV file for further analysis in subsequent notebooks.

This initial data collection phase establishes the foundation for the predictive modeling that follows in the complete project.

# Lab 02: SpaceX Falcon 9 First Stage Landing Prediction: Web Scraping

In this notebook, I utilize web scraping techniques to gather historical launch data for Falcon 9 rockets from Wikipedia. This complements the API data collected previously and provides an alternative data source for the landing prediction project.

## Key Components and Workflow:

1. **Environment Setup**: I imported necessary libraries including BeautifulSoup for HTML parsing, requests for HTTP retrieval, and pandas for data manipulation.

2. **Helper Functions Creation**: I defined several utility functions to:
   - Extract date and time information from table cells
   - Parse booster version details
   - Identify landing outcomes
   - Extract payload mass information
   - Clean and format column headers

3. **Wikipedia Page Retrieval**: I accessed a specific version of the "List of Falcon 9 and Falcon Heavy launches" Wikipedia page from June 9, 2021 to ensure data consistency.

4. **HTML Parsing**: Using BeautifulSoup, I:
   - Located the specific HTML tables containing launch information
   - Extracted column names from table headers
   - Created a structured dictionary to store the parsed data

5. **Data Extraction**: I systematically extracted data from each row of the launch tables, handling various edge cases such as:
   - Missing values
   - Inconsistent formatting
   - Complex nested HTML structures
   - Reference annotations

6. **Data Organization**: Compiled all extracted information into a dictionary with keys corresponding to launch attributes like flight number, launch site, payload details, orbit type, and landing outcomes.

7. **DataFrame Creation**: Converted the structured dictionary into a pandas DataFrame for easier analysis and manipulation.

8. **Data Export**: Saved the web-scraped dataset to a CSV file named 'spacex_web_scraped.csv' for integration with the prediction model in later stages.

This web scraping approach provides a complementary dataset that can be cross-referenced with the API data to validate information and fill in any potential gaps.

# Lab 03: SpaceX Falcon 9 First Stage Landing Prediction: Data Wrangling

In this notebook, I perform exploratory data analysis and create classification labels for the SpaceX Falcon 9 landing prediction model. This step transforms raw launch data into a format suitable for machine learning.

## Key Components and Workflow:

1. **Initial Data Exploration**: I loaded the dataset created in the previous steps and analyzed its structure, checking for missing values and identifying numerical versus categorical columns.

2. **Launch Site Analysis**: I analyzed the distribution of launches across different SpaceX launch facilities, providing insight into which sites have been used most frequently for Falcon 9 missions.

3. **Orbit Type Examination**: I investigated the target orbits for each mission, identifying the most common orbit types (such as GTO, LEO, ISS) used in SpaceX launches and their relative frequencies.

4. **Landing Outcome Assessment**: I performed a detailed analysis of the mission outcomes, distinguishing between various landing scenarios:
   - Ocean landings (successful and failed)
   - Return to Launch Site (RTLS) landings (successful and failed)
   - Autonomous Spaceport Drone Ship (ASDS) landings (successful and failed)
   - Complete landing failures

5. **Binary Label Creation**: I transformed the complex landing outcome categories into a binary classification problem by:
   - Identifying all unsuccessful landing outcomes
   - Creating a binary label (0 for unsuccessful, 1 for successful)
   - Adding this classification as a new column in the dataset

6. **Success Rate Calculation**: I calculated the overall success rate of SpaceX first stage landings, providing a baseline metric for model performance evaluation.

7. **Processed Data Export**: I saved the enhanced dataset with the newly created classification labels to a CSV file for use in building predictive models in subsequent notebooks.

This data wrangling step is crucial for converting the raw launch outcome data into a structured format that can be used for supervised machine learning algorithms in the prediction phase of the project.

# Lab 04: SpaceX Falcon 9 First Stage Landing Prediction: SQL Exploratory Data Analysis

In this notebook, I leverage SQL to perform in-depth exploratory data analysis on the SpaceX launch dataset. This structured query approach allows for targeted insights about launch patterns and landing outcomes.

## Key Components and Workflow:

1. **Database Setup**: I established a SQLite database connection and imported the SpaceX dataset, creating a clean table structure for SQL querying.

2. **Launch Site Investigation**: I identified all unique launch sites in the dataset and analyzed the frequency of launches from each location, with special attention to Cape Canaveral Air Force Station.

3. **Payload Analysis**: My SQL queries revealed insights about payload characteristics:
   - Total mass carried for NASA's Commercial Resupply Services missions
   - Average payload capacity of different Falcon 9 booster versions
   - Identification of boosters that carried maximum payload mass

4. **Landing Success Milestones**: I determined key accomplishments in SpaceX's landing technology:
   - Date of the first successful ground pad landing
   - Boosters capable of successful drone ship landings with medium-weight payloads (4000-6000 kg)

5. **Mission Outcome Statistics**: I calculated the total counts of successful versus failed missions and ranked different landing outcomes by frequency.

6. **Temporal Pattern Analysis**: I examined specific time periods to identify trends:
   - Failed drone ship landing attempts in 2015, organized by month
   - Landing outcome frequencies between June 2010 and March 2017

7. **Comparative Performance Analysis**: My queries enabled comparison between different booster versions, landing methods, and mission parameters to identify factors potentially influencing landing success.

8. **Comprehensive Results Synthesis**: I concluded with a summary of findings that provides valuable context for developing predictive models of landing success.

This SQL-based exploration complements the previous data collection and wrangling efforts by providing structured, quantitative insights into the factors that may influence first stage landing outcomes. The analytical approach demonstrates how database queries can extract meaningful patterns from complex aerospace operations data.

# Lab 05: SpaceX Falcon 9 First Stage Landing Prediction: Data Visualization and Feature Engineering

In this notebook, I employ advanced data visualization techniques to uncover patterns and relationships in the SpaceX launch data, followed by feature engineering to prepare for machine learning model development.

## Key Components and Workflow:

1. **Visualization Environment Setup**: I configured a robust visualization toolkit including Pandas, Matplotlib, and Seaborn libraries to create informative visual representations of the SpaceX launch data.

2. **Launch Success Pattern Analysis**: I created a series of visualizations to identify relationships between launch success and various factors:
   - Flight number vs. payload mass, revealing increased success rates with more flight experience
   - Launch site performance comparison, identifying sites with higher success rates (KSC LC-39A and VAFB SLC 4E at ~77%)
   - Orbit type success rates, demonstrating varying difficulty levels for different orbit targets

3. **Multi-dimensional Visual Exploration**: I designed plots that examine interactions between multiple variables:
   - Flight number vs. launch site, showing experience-based improvements
   - Payload mass vs. launch site, revealing site-specific payload capacity limitations
   - Flight number vs. orbit type, identifying orbit-specific success patterns
   - Payload mass vs. orbit type, showing how mass affects success rates for different orbits

4. **Temporal Trend Analysis**: I extracted and plotted year-by-year success rates from 2013-2020, confirming a clear upward trend in landing success as SpaceX refined their technology and procedures.

5. **Feature Selection**: Based on the insights from visualization, I selected key variables that showed significant relationships with landing outcomes for use in predictive modeling.

6. **Categorical Variable Transformation**: I applied one-hot encoding to convert categorical variables (Orbit, LaunchSite, LandingPad, Serial) into numerical format suitable for machine learning algorithms.

7. **Data Preparation and Export**: I standardized all features to a consistent data type (float64) and exported the engineered dataset for subsequent modeling stages.

This visualization and feature engineering work bridges the gap between data collection and model development, transforming raw data into structured, algorithm-ready inputs while providing visual confirmation of important patterns that will inform the prediction approach. The insights gained from this analysis help explain why certain launches succeed or fail, creating a foundation for building accurate predictive models.

# Lab 06: SpaceX Falcon 9 First Stage Landing Prediction: Interactive Dashboard

In this notebook, I develop an interactive web dashboard using Dash and Plotly to allow stakeholders to explore the SpaceX launch data and understand the factors affecting landing success rates.

## Key Components and Workflow:

1. **Development Environment Configuration**: I set up the necessary infrastructure by:
   - Installing required libraries (Dash, Plotly)
   - Importing essential components for web application development
   - Configuring the environment to run a web server within the notebook

2. **Data Preparation**: I loaded the processed SpaceX dataset and calculated key metrics to drive the visualizations:
   - Determining minimum and maximum payload masses for range selection
   - Extracting unique launch sites for dropdown options
   - Organizing the data in a format suitable for interactive visualization

3. **Dashboard Layout Design**: I created a comprehensive dashboard layout with:
   - A clear, professional title and styling
   - A dropdown menu for selecting specific launch sites or viewing aggregated data
   - A pie chart visualization area for success rate analysis
   - A payload range selector implemented as an interactive slider
   - A scatter plot visualization area for exploring payload mass vs. success relationships

4. **First Interactive Component**: I implemented a callback function for the launch site dropdown that creates:
   - A pie chart showing successful launches by site when "All Sites" is selected
   - A pie chart displaying success vs. failure ratio when a specific site is selected

5. **Second Interactive Component**: I developed a more complex callback for the scatter plot that:
   - Updates based on both the selected launch site and payload range
   - Shows the relationship between payload mass and mission success
   - Colors data points by booster version to provide additional insight
   - Dynamically adjusts the chart title based on user selections

6. **Interaction Logic Implementation**: I connected the user interface elements through callback functions that:
   - Respond to user input changes in real-time
   - Filter data appropriately based on multiple inputs
   - Update visualizations with properly formatted titles and legends
   - Maintain consistent color schemes for visual coherence

7. **Dashboard Deployment**: I executed the web application with debugging enabled, allowing users to interact with the dashboard directly in the notebook interface.

This interactive dashboard brings together the insights from all previous analysis steps, presenting them in an accessible format that allows users to explore the data themselves. By providing both high-level summaries and detailed filtering capabilities, the dashboard enables a deeper understanding of the factors that contribute to successful Falcon 9 first stage landings, a critical component of SpaceX's cost-saving strategy.

# Lab 07: SpaceX Falcon 9 First Stage Landing Prediction: Machine Learning Models

In this notebook, I develop and evaluate multiple machine learning models to predict whether a SpaceX Falcon 9 first stage will land successfully. This prediction has significant economic implications since SpaceX's ability to reuse first stages contributes to their launch cost advantage of $62 million versus competitors' $165 million.

## Key Components and Workflow:

1. **Data Preparation**: I loaded the previously processed SpaceX launch data, confirmed the class balance (approximately 2/3 successful landings), and performed necessary preprocessing:
   - Extracted relevant predictive features excluding flight number
   - Standardized all features using StandardScaler
   - Split the data into training (70%) and test (30%) sets with fixed random seed

2. **Logistic Regression Model**: I implemented a logistic regression classifier with extensive hyperparameter tuning:
   - Optimized regularization strength, penalty type, and solver algorithm using GridSearchCV
   - Performed 10-fold cross-validation to ensure robust hyperparameter selection
   - Evaluated model performance using accuracy and F1 score metrics
   - Analyzed the confusion matrix to identify false positive errors

3. **Support Vector Machine**: I developed an SVM classifier with kernel optimization:
   - Tested multiple kernel functions (linear, RBF, polynomial, sigmoid)
   - Tuned regularization parameter C and kernel bandwidth gamma
   - Achieved good performance but slightly below logistic regression
   - Observed an additional false negative error not present in the logistic model

4. **Decision Tree Classifier**: I implemented a decision tree with comprehensive parameter tuning:
   - Optimized split criteria, tree depth, minimum sample thresholds, and feature selection
   - Observed high training accuracy but significantly lower test performance
   - Identified clear overfitting issues despite cross-validation efforts

5. **K-Nearest Neighbors Classifier**: I built a KNN model with distance optimization:
   - Tuned the number of neighbors, algorithm implementation, and distance metric
   - Achieved competitive performance similar to SVM
   - Analyzed error patterns through confusion matrix visualization

6. **Comparative Model Evaluation**: I conducted a systematic comparison of all models:
   - Created visualization of test accuracy and F1 scores across all classifiers
   - Identified logistic regression as the best performing model
   - Analyzed error patterns to understand model limitations
   - Provided recommendations for practical implementation

7. **Results Interpretation**: The analysis revealed that logistic regression provided the best balance of performance and simplicity, suggesting the relationship between launch parameters and landing success may be relatively linear, despite attempts to capture non-linear patterns with more complex models.

This machine learning analysis completes the SpaceX landing prediction project workflow, demonstrating that relatively simple models can effectively predict landing outcomes. The developed model could be used by competing aerospace companies to estimate SpaceX launch costs or by investors to assess technological maturity in the launch industry.
