# Medical Marijuana Group Final Project

### Selected Topic
Medical Marijuana Strain Selection Analysis

![Medical_Marijuana_Group_Final_Project](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Medical_Marijuana_Group_Final_Project.gif)

#### Presentation Link
https://docs.google.com/presentation/d/1T1nRURT1p7oJN2ruLPGVpZXlen5MgNw84jo5yZJZMVY/edit?usp=sharing

#### Dashboard Link
https://public.tableau.com/app/profile/jemi.shieh/viz/MedicalMarijuanaGroupFinalProjectDashboard/MedicalMarijuanaGroupFinalProjectStrainSelectionAnalysis?publish=yes

#### Webpage Links
Dashboard:
https://mmg-tableau-dashboard.herokuapp.com/

Strain Selector:
https://mmg-strain-selector.herokuapp.com/

### Reason for Selecting Topic:
Marijuana has long been a controversial topic in the US, at one point in history it was perfectly legal. It was grown, sold, and consumed openly. Benjamin Franklin, Thomas Jefferson, and James Madison to name a few had cultivated hemp in the 1700's. The marijuana crop has long been a part of the US economy and with recently passed legislation marijuana is once again becoming a part of the US economy. Cannabis has long been known to have medicinal qualities going back many centuries from the Egyptians all the way to the silk road and was grown in much of Asia thousands of years ago. However only recently have scientists and medical professionals been able to quantify and measure the medicinal properties of marijuana, there are plenty well documented medical applications for Marijuana. Doctors have been prescribing medicinal marijuana to treat, depression, stress, nausea, epilepsy, seizures, glaucoma, and numerous other ailments. There have been promising developments in the field of cancer research with several studies showing that medicinal marijuana can help to alleviate certain symptoms from certain types of cancer and to help mitigate the side effects of chemotherapy. 

There is one issue however, since marijuana has been illegal for so long many patients have no firsthand experience with the plant and many of them are trying it for the first time when a doctors prescribes it as a treatment. The goal of this project is to see if there is a correlation between the various strains of medical marijuana and the ailments they are intended to treat. If a relationship between strain and ailment does exist then it may be possible to create an easy to use engine for medical marijuana patients to identify which strains will best treat their ailments.  

### Questions We Hope to Answer:
1. Can we create a neural network that can accurately classify strains?
2. Can the model correctly match strains with ailments treated?
3. Can we create a strain selector to help patients choose the proper strain based on their ailments?

### Hypothesis
#### Null Hypothesis: Sativa, Indica and Hybrid strains share a correlation with certain effects that are best suited for the treatment of patient ailments.
Can we find a positive correlation between the strain type and ailments, for example will strains that fall under the Sativa category treat stress, and depression? Will strains that fall under the Indica category treat ailments like nausea and lack of sleep?

#### Alternate Hypothesis: There is no relationship between strains and their effects.
Determine which medical marijuana strains are best suited as treatment for specific ailments by analyzing their chemical composition and characteristics such as flavor and effects by creating a neural network that allows us to recognize similar characterizes in strains of cannabis that would best work to help relieve a whole array of symptoms ranging from depression, stress, pain, and inflammation, among others.

### Team Role Distribution
* Triangle - Machine Learning Model - David Bastien
* Square - GitHub Repository - Paul Erlic
* X - Technology Architect - Ashley Mayes
* Circle - Database Integration - Jemi Shieh

### Resources
* The Kushy cannabis dataset is a collection of tabular data from different sectors of the industry, from strains to products to lab results:<br />
https://github.com/kushyapp/cannabis-dataset/blob/master/Dataset/Strains/strains-kushy_api.2017-11-14.csv
* The Washington cannabis dataset contains over 215,000 laboratory measurements, performed at six different labs, of retail cannabis products from Washington State, originally published on March 14, 2018 in Nature. Harvard Replication Data: <br />
https://www.nature.com/articles/s41598-018-22755-2 <br />
https://dataverse.harvard.edu/file.xhtml?persistentId=doi:10.7910/DVN/E8TQSD/XT7UNM&version=2.0
* The US state medical marijuana laws dataset: <br /> 
https://www.ncsl.org/research/health/state-medical-marijuana-laws.aspx

### Technologies Used
* Data Analysis: Excel, Python, Pandas and SQL used to perform data exploration, cleaning and preprocessing the data.
* Database Storage: PostgreSQL is the storage database and psycopg2 (import model data from database) and SQLAlchemy (export data cleaning/model output to database) used to interface and connect the model with the database in Python.
* Machine Learning: TensorFLow, KerasTuner, and SciKitLearn machine learning libraries used to create a Deep Learning Neural Network using Python in Jupyter Notebook.
* Dashboard: Tableau, JavaScript, HTML, Bootstrap, d3, PHP, Heroku and GitHub Pages used to create a fully functioning and interactive dashboard and webpages.

### Project Description
#### Data Exploration and Cleaning 
* Our first step in the ETL workflow was to index, parse, and remove any columns or rows that were not pertinent to our projects goals this process was done in Excel. After this step we chose to merge the two data sets into one dataset, merging was performed in PostgresSQL and the dataset was exported as a CSV file for simpler handling. We also used Excel to get a preliminary feel for the data in order to better understand what if any underlying patterns existed in the data. 
 
* The data was then cleaned again in Pythons/Pandas the purpose of the extra cleaning step was to replace all categorical object null values with “None” and all continuous numerical null values with “0”. Doing this to the data allowed us more flexibility when analyzing the 'ailments' as some of them were empty in the original data. The same applied to the empty chemotype variables, rather than drop them from the analysis we transformed them to a zero. Neither of the transformations to data will skew the results in any meaningful way because all we were doing was creating place holders for the original empty cells in the dataset. 

![Screen Shot 105](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(105).png)

![Screen Shot 106](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(106).png)

![Screen Shot 107](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(107).png)
 
* We also created 5 new calculated fields/columns and added them to the dataset using Pandas in Python, these calculate columns allowed us to explore some potential patterns in ratios between several variables in the data set.
* Bi-Variate Correlation Statistical Analysis performed using heat maps to find relationships between features and identify dependent variables.

![Screenshot 123](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(123).png)
  
#### Database Integration
* Our database is hosted in PostgresSQL to store the static data for our analysis.
* Reading and writing operations in PostgresSQL databases are fast and efficient.
* We have four tables in the database which can be seen in ERD below.
 
 ![mmg_sql_erd pgerd](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/mmg_sql_erd.pgerd.png)

* PostgreSQL connects to the model via psycopg2 to import data and SQLAlchemy to export data.

![Screenshot 112](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(112).png)

* PostgreSQL connects to the model via SQLAlchemy to export data.

![Screenshot 120](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(120).png)
      
#### Machine Learning Model 
##### Deep Learning Neural Network
Neural networks are a set of algorithms modeled after the human brain. They are an advanced form of machine learning that recognizes patterns and features in input data and provides a clear quantitative output. In its simplest form, a neural network contains layers of neurons, which perform individual computations. These computations are connected and weighed against one another until the neurons reach the final layer, which returns a numerical result, or an encoded categorical result.

A neural network with more than one hidden layer is known as a deep neural network. Deep neural networks function similarly to the basic neural network, with one major exception. The outputs of one hidden layer of neurons (that have been evaluated and transformed using an activation function) become the inputs to additional hidden layers of neurons. As a result, the next layer of neurons can evaluate higher order interactions between weighted variables and identify complex, nonlinear relationships across the entire dataset. These additional layers can observe and weight interactions between clusters of neurons across the entire dataset, which means they can identify and account for more information than any number of neurons in a single hidden layer.

Deep neural network models also are commonly referred to as deep learning models due to their ability to learn from example data, regardless of the complexity or data input type. Just like humans, deep learning models can identify patterns, determine severity, and adapt to changing input data from a wide variety of data sources. Compared to basic neural network models, which require a large number of neurons to identify nonlinear characteristics, deep learning models only need a few neurons across a few hidden layers to identify the same nonlinear characteristics.

Source: https://courses.bootcampspot.com/courses/949/pages/19-dot-1-1-what-is-a-neural-network?module_item_id=342279 <br />
Source: https://courses.bootcampspot.com/courses/949/pages/19-dot-4-1-unleash-the-hidden-potential-of-neural-networks?module_item_id=342386

![deep_nn.png](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/deep_nn.png)

Source: University of Cincinnati https://healthitanalytics.com/features/what-is-deep-learning-and-how-will-it-change-healthcare

##### Limitations of the Deep Learning Neural Network
* Requires larger data volumes than other models
* High computational power and cost to train due to complex data models running on multiple expensive GPUs and machines
* Highly complex and esoteric given no standard theory
* Difficult to comprehend and interpret results given black box nature 
* Prone to overfitting

##### Benefits of the Deep Learning Neural Network
* Ability to learn independently in real-time
* Flexible and can be applied to multiple data types and current and future applications
* Features automatically deduced/optimally tuned for desired result so outputs not limited to provided inputs
* Features not required to be extracted in advance
* Data stored in neural network itself rather than a database 
* Allows for multiple parallel computations using GPUs scalable for large data volumes
* Larger data volumes actually result in enhanced performance   
* Produces output regardless of fault/error detection with model/data
* Ideal for multiclass classification with large number of inputs/outputs
* Effective at detecting complex, nonlinear relationships
* Greater tolerance for messy data and can learn to ignore noisy characteristics in data

##### Preprocessing the Data
* Kushy and Washington datasets indexed by primary key, parsed text into columns, reduced unnecessary columns and rows using Excel
* Datasets uploaded into PostgreSQL tables, joined/merged and exported as CSV
* ETL cleaning performed using Pandas in Python to create missing value heatmaps and find/replace all categorical object null values with “None” and all continuous numerical null values with “0”
* Created 5 new calculated fields/columns added to dataset using Pandas in Python 
* Bi-Variate Correlation Statistical Analysis performed using heat maps to find relationships between features and identify dependent variables
* Exported cleaned/calculated data back to PostrgreSQL using SQLAlchemy to be imported into the model using psycopg2
* Data imported into model from PostgreSQL using psycopg2 and preprocessed in Python using Pandas (shape, dtypes, info, describe, duplicates, unique, value_counts, binning, categorical, get_dummies), SciKitLearn (LabelEncoder, OneHotEncoder, StandardScaler), and split into dependent target and independent feature variables
 
##### Feature Engineering, Selection, and Training/Testing Split
* Preliminary feature engineering included the creation of five calculated fields: ailment_count, effects_count, flavor_count, thc_max/cbd_max, cbd_max/thc_max 
* Preliminary feature reduction/selection eliminated identification, location and other non-strain specific columns as it was determined there was no correlation with strains or ailments which would help the model make predictions. 
* The dependent target variable was determined to be ailment_1 (y) comprising 9 output classes and the remaining features independent variables (X) comprising 316 input variables which were all descriptive characteristics and testing results directly related to a specific strain profile.
* The features and target sets were split into standard training (75%) and testing (25%) sets to train and validate the model. The purpose is to prevent overfitting and accurately evaluate the model.
* The model was compiled, fit, trained and tested in TensorFlow using a 75%/25% split of the data over 100 epochs.

##### Analysis
We built and tested six different machine learning models when analyzing the data to predict accuracy and chose the Deep Learning Neural Network as it produced the most accurate results and was the most appropriate algorithm for multiclass classification of our large number of input (190) and output variables (9): 
* K-means clustering - 66.76% accuracy
* K-means clustering with Principal Component Analysis - 51.47% accuracy
* Random Forest Multiclass Classifier - 67.96% accuracy
* Simple Neural Network - 85.64% accuracy, 0.70 loss
* Deep Learning Neural Network - 87.85% accuracy, 0.67 loss
* Deep Learning Neural Network with KerasTuner optimization - 88.40% accuracy, .60 loss

##### Results
* The Deep Learning Neural Network was 87.85% accurate with KerasTuner optimization leading to accuracy of 88.40%.
* The results were fairly easy to interpret from the model accuracy score despite the black box nature of neural networks.
* We chose the model that produced the most accurate results and was the most appropriate algorithm for multiclass classification of our large number of input (190) and output variables (9).
* A simple neural network entailing less computational cost and resources was 85.64% accurate.
* The model is built and trained to reproduce similarly accurate results each time it is run.

##### Confusion Matrix
The model correctly classified strains according to their primary ailment treated with an accuracy score of 87.85%. This would assist in the creation of a strain selector to help patients choose an appropriate medicinal strain based on their ailments.
The model’s weighted average precision and recall (sensitivity) is 84% and 88%, respectively, meaning 84% of the retrieved instances were relevant and 88% of all relevant instances were retrieved.

![Screenshot 150](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(150).png)
  
![Screenshot 151](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(151).png)

### Future Analysis Recommendations
* Further model optimization, such as additional binning of categorical and numerical data and features
* Perform chi-square test statistical analysis to determine most relevant features
* Perform natural language processing analysis on ailment, effect and flavor tags
* Perform strain image clustering and classification analysis

### Project Improvement Recommendations 
* Create larger, more complete and updated dataset using the Cannabis Reports Database API
* Add strain images to dataset for identification and analysis 
* Further model optimization to improve accuracy and reduce loss
* Create improved webpages for the project dashboard and strain selector search filter with drop-down menus
* Adhere to improved GitHub guidelines for project development, review and implementation workflow

### Dashboard
https://public.tableau.com/app/profile/jemi.shieh/viz/MedicalMarijuanaGroupFinalProjectDashboard/MedicalMarijuanaGroupFinalProjectStrainSelectionAnalysis?publish=yes

#### Webpage Links
Dashboard:
https://mmg-tableau-dashboard.herokuapp.com/

![Screenshot (125)](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(125).png)

Strain Selector:
https://mmg-strain-selector.herokuapp.com/

![Screenshot (126)](https://github.com/paulerlic/medical-marijuana-group/blob/main/Images/Screenshot%20(126).png)

#### Tools Used to Create Final Dashboard
* Tableau, JavaScript, Tableau JavaScript API, HTML, Bootstrap, d3, Heroku, PHP, GitHub Pages

#### Description of Interactive Elements
* All Tableau visualizations include interactive legend filters to sort the data and explore different patterns we found in the medical marijuana data.
* Tableau US Legalization Map and Strain Selector include interactive search filters.
* Web app Strain Selector includes interactive search filter
