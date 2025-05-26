# SpaceX Falcon 9 First Stage Landing Prediction

## Project Overview

The commercial space industry is rapidly evolving with the goal of reducing the high cost of space travel. SpaceX has pioneered reusable rocket technology, cutting launch costs significantly. This project aims to predict whether the first stage of the Falcon 9 rocket will successfully land, impacting overall launch expenses. Machine learning models analyze publicly available launch data to forecast first-stage landing outcomes, enabling cost optimization without relying on traditional rocket science methods.

## Who Will Benefit and Why?

This project benefits aerospace companies, government agencies, researchers, and investors by providing actionable insights into launch success prediction and cost management.

* **Aerospace Companies:** Improve rocket reusability strategies, reducing operational costs.
* **Government Agencies:** Enhance mission planning and budget forecasting with predictive analytics.
* **Researchers and Data Scientists:** Explore applications of machine learning in aerospace launch analysis.
* **Investors and Policymakers:** Make informed decisions on funding and regulations based on reusable rocket efficiency.

## Data Source

The dataset combines SpaceX launch records obtained through the SpaceX REST API and additional launch data scraped from Wikipedia. This real-world dataset covers detailed Falcon 9 launch information, including flight numbers, payloads, launch sites, orbits, and landing outcomes.

## How the Project Was Executed

* **Data Collection:** Retrieved launch data using SpaceX API and scraped Wikipedia with BeautifulSoup.
* **Data Wrangling & EDA:** Cleaned data, classified mission outcomes (success/failure), and explored key attributes like launch sites and orbits.
* **Visualization:** Created scatter plots and trend charts to understand relationships among payloads, launch sites, flight numbers, and success rates.
* **SQL Analysis:** Stored data in SQLite; extracted insights such as total payload mass for NASA missions and dates of landmark landings.
* **Geospatial Mapping:** Used Folium to map launch sites relative to infrastructure like railways, highways, coastlines, and cities for safety and logistics evaluation.
* **Dashboard Development:** Built an interactive Plotly Dash dashboard to visualize launch success percentages and payload success relationships.
* **Predictive Modeling:** Trained multiple classifiers (Logistic Regression, SVM, Decision Tree, KNN) with hyperparameter tuning via GridSearchCV.

## Key Findings

**1. Which launch site is the most active and successful?**

* CCAFS SLC-40 leads in activity with success rates rising alongside flight numbers.

**2. How does payload mass vary by launch site?**

* VAFB SLC 4E handles lighter payloads (up to 10,000 kg), whereas other sites support heavier loads.

**3. Which orbits have the highest success rates?**

* ES-L1, GEO, and HEO orbits achieved 100% success; GTO orbit had the lowest success (50%), and SO orbit recorded no successful landings.

**4. Does flight experience improve success rates by orbit?**

* Yes, success rates increase with flight number for LEO orbits, but no clear pattern exists for GTO.

**5. Is payload mass linked to orbit success?**

* Heavier payloads have higher success in Polar, LEO, and ISS orbits; GTO orbit shows no clear correlation.

**6. How has launch success evolved over time?**

* SpaceX’s launch success has steadily improved since 2013, with marked gains between 2013 and 2020.

**7. What geospatial factors affect launch sites?**

* Sites are near key infrastructure (railways, highways, coastlines) yet maintain safe distances from populated areas.

**8. Which site shows the highest success on the dashboard?**

* KSC LC-39A stands out with a 76.9% launch success rate.

**9. Which machine learning model performed best?**

* Decision Tree Classifier achieved the highest accuracy (0.8889) with zero false negatives, outperforming Logistic Regression, SVM, and KNN.

## Conclusion

Machine learning effectively predicts Falcon 9 first-stage landing success using launch data. The Decision Tree model provides robust accuracy and reveals key success patterns tied to launch sites, payloads, orbits, and experience. These insights offer valuable guidance for improving rocket reuse strategies and cost efficiency.

## Recommendations

Future work may include integrating weather and trajectory data, exploring advanced modeling techniques like neural networks, enabling real-time prediction dashboards, and expanding analysis to other rocket types such as Falcon Heavy and Starship.

## Acknowledgment

This project is part of the IBM Data Science Capstone Project within the IBM Data Science Professional Certificate on Coursera. The project framework and data were provided by IBM; implementation was conducted independently.

## Author

Qazi Fabia Hoq
