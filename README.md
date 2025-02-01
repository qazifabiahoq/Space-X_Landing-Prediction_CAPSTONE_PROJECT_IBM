# **SpaceX Falcon 9 First Stage Landing Prediction**  

## **Project Overview**  
The commercial space industry is rapidly evolving, with companies striving to make space travel more cost-effective. SpaceX has revolutionized spaceflight by developing reusable rockets, significantly reducing launch costs. The Falcon 9 rocket, advertised at $62 million per launch, is much cheaper than competitors, mainly due to its reusable first stage.  

This project focuses on predicting whether the first stage of a Falcon 9 rocket will successfully land, thereby determining launch costs. Instead of relying on rocket science, machine learning models are used to analyze public launch data and predict first-stage reuse.  

The full report detailing all findings, methodologies, and results is available in the **"report.pdf"** file within the **"report"** folder of this repository.  

## **Who This Project Is For?**  
This project is valuable for **aerospace companies, government agencies, and researchers** involved in space exploration and rocket launch cost optimization.  

- **Aerospace Industry**: Companies like SpaceX, Blue Origin, and Rocket Lab can use similar predictive models to enhance rocket reusability, reducing costs.  
- **Government Agencies**: Organizations such as **NASA and national space programs** can benefit from predictive analysis to improve mission planning and budgeting.  
- **Researchers & Data Scientists**: Those studying machine learning applications in aerospace can gain insights into how data-driven methods enhance launch success predictions.  
- **Investors & Policymakers**: Understanding cost efficiencies in reusable rockets can guide funding and regulatory decisions for commercial spaceflight.  

## **Data Collection**  

### **1. SpaceX API**  
- Data was collected via a **GET request** to the SpaceX API.  
- The API response was converted into a **Pandas DataFrame** using `.json_normalize()`.  
- Data cleaning included handling missing values and standardizing formats.  

### **2. Web Scraping**  
- **BeautifulSoup** was used to scrape Falcon 9 launch records from Wikipedia.  
- The extracted HTML table data was parsed and structured into a Pandas DataFrame for further analysis.  

## **Data Wrangling & Exploratory Data Analysis (EDA)**  
- Launch sites were analyzed using `.value_counts()` to determine the number of launches per site.  
- The frequency of each orbit type was examined.  
- Mission outcomes were categorized into **landing success (1)** and **failure (0)** for machine learning.  
- Results were exported as a **CSV file** for modeling.  

## **Data Visualization**  
- Visualizations explored relationships between **flight numbers, launch sites, payloads, and success rates**.  
- Scatter plots analyzed **payload mass vs. orbit type** and **flight number vs. launch site**.  
- Yearly trends in launch success rates were also plotted.  

## **SQL-Based EDA**  
- The dataset was stored in a **SQLite database** and analyzed using SQLAlchemy.  
- Key insights extracted:  
  - **Total payload mass** carried by NASA (CRS) missions: **48,213 kg**.  
  - **Average payload mass** for booster version **F9 v1.1**: **2,928.4 kg**.  
  - **Date of first successful ground landing**: **July 22, 2018**.  

## **Geospatial Analysis**  
- Mapped launch sites with **Folium** and classified them based on landing success.  
- Calculated distances to key features:  
  - **Railways**: CCAFS LC-40 is near NASA Railway, aiding equipment transport.  
  - **Highways**: KSC LC-39A is close to Kennedy Parkway North for logistical efficiency.  
  - **Coastlines**: KSC LC-39A and CCAFS LC-40 benefit from safe launch trajectories over the ocean.  
  - **Cities**: Launch sites are strategically distant from urban areas for safety.  

## **Plotly Dash Dashboard**  
An interactive dashboard was developed using **Plotly Dash** to visualize:  
- **Launch success percentages** across different sites.  
  - **KSC LC-39A:** 49%  
  - **CCAFS SLC-40:** 12.5%  
  - **CCAFS LC-40:** 29.2%  
  - **VAFB SLC-4E:** 16.7%  
- **Scatter plots** showing payload mass vs. success rate.  
- **KSC LC-39A** had the highest launch success rate (**76.9%** success, **23.1%** failure).  
- **Low-weight payloads had a higher success rate** compared to heavier payloads.  

## **Machine Learning & Predictive Analysis**  

### **Model Training**  
- Data was split into **training and testing sets**.  
- Feature engineering and **GridSearchCV** were used for hyperparameter tuning.  
- Multiple classification models were evaluated:  
  - **Logistic Regression**  
  - **Support Vector Machine (SVM)**  
  - **Decision Tree Classifier**  
  - **K-Nearest Neighbors (KNN)**  

### **Best Model: Decision Tree Classifier**  
- **Accuracy:** **0.8889 (Highest among all models)**  
- **Confusion Matrix Performance:**  
  - **True Positives (Landed Correctly):** **12**  
  - **True Negatives (Did Not Land Correctly):** **4**  
  - **False Positives:** **2**  
  - **False Negatives:** **0** (Indicating high accuracy in predicting successful landings)  

### **Model Comparison**  
| Model | Accuracy | False Positives | False Negatives |  
|--------|------------|----------------|----------------|  
| **Logistic Regression** | **0.8333** | **0** | **3** |  
| **SVM** | **0.8333** | **0** | **3** |  
| **Decision Tree** | **0.8889** | **2** | **0** |  
| **KNN** | **0.8333** | **0** | **3** |  

The **Decision Tree Classifier** was the best-performing model because:  
- It achieved the **highest accuracy (0.8889)**.  
- It correctly predicted **all successful landings (0 false negatives)**.  
- It outperformed Logistic Regression, SVM, and KNN.  

## **Key Findings**  

### **1. Flight Number vs. Launch Site**  
- **CCAFS SLC-40 is the most active launch site** with increasing success as flight numbers rise.  

### **2. Payload vs. Launch Site**  
- **VAFB SLC 4E specializes in lighter payloads (≤10,000 kg)**, while other sites support heavier payloads.  

### **3. Success Rate vs. Orbit Type**  
- **Highest success (100%)**: ES-L1, GEO, and HEO orbits.  
- **Lowest success (50%)**: GTO orbit.  
- **No successful missions**: SO orbit.  

### **4. Flight Number vs. Orbit Type**  
- **LEO orbit success rate increases** with flight number.  
- **GTO orbit shows no clear trend** in relation to flight number.  

### **5. Payload vs. Orbit Type**  
- **Polar, LEO, and ISS orbits favor heavier payloads** with higher success rates.  
- **GTO orbit has no clear relationship between payload mass and success.**  

### **6. Yearly Launch Success Trend**  
- **Steady improvement** in SpaceX launch success rates since **2013**, especially from **2013–2020**.  

### **7. Geospatial Insights**  
- Launch sites are positioned **close to key infrastructure** (railways, highways, coastlines) but maintain a **safe distance from urban areas**.  

### **8. Dashboard Insights**  
- **KSC LC-39A had the highest launch success rate (76.9%)**.  
- **Lighter payloads had a higher success rate** than heavier payloads.  

### **9. Best Predictive Model**  
- **Decision Tree Classifier** was the best model with **0.8889 accuracy** and no false negatives.

## **Future Improvements**  
This project provides a strong foundation for predicting Falcon 9 first-stage landings. Potential future enhancements include:  

- **Model Optimization**: Exploring deep learning techniques such as neural networks to improve prediction accuracy.  
- **Feature Engineering**: Incorporating additional factors like weather conditions, wind speed, and launch trajectory data.  
- **Real-Time Predictions**: Developing a live dashboard that integrates new SpaceX launch data for continuous model updates.  
- **Broader Application**: Extending the model to other rocket types, including Falcon Heavy and Starship, for wider applicability.  

## **Conclusion**  
This project demonstrates how machine learning can predict Falcon 9 first-stage landings using historical launch data. **The Decision Tree model provided the highest accuracy** and identified key launch success patterns.  

## **Acknowledgment**  
This project is part of the **IBM Data Science Capstone Project**, assigned as part of the **IBM Data Science Professional Certificate** course on **Coursera**.  

The project task and outline were provided by **IBM**, while the implementation and completion were independently carried out.  

## **Author**  
**Qazi Fabia Hoq**  


🚀 **For a more detailed analysis, check the full report in**: **"report.pdf" (located in the "report" folder of this repository).**  
