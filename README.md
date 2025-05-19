
<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Opioid Risk Radar

Final project for the Building AI course

<p align="center">
  <img src="Opioid%20Risk%20Radar.png" width="400">
</p>
<p align="center"><sub><em>Infographic created by the author using Canva.</em></sub></p>



## Summary

Opioid Risk Radar is a community-focused AI dashboard designed to support both public health professionals and individuals affected by the opioid crisis. It predicts overdose risk at the ZIP code or county level by analyzing real-time public health, prescription, and emergency response data. By combining logistic regression and clustering algorithms, the tool detects statistically significant spikes in opioid-related incidents and visualizes emerging hotspots on an interactive heatmap.

The platform is built for dual use: public health agencies and outreach organizations can use it to monitor trends, identify rising-risk areas, and strategically deploy resources like naloxone, mobile clinics, and educational outreach. At the same time, individual users can access localized alerts, find nearby support services, and connect with others through anonymous tools. The goal of Opioid Risk Radar is to serve not only as a tool for early intervention, but also as a platform that strengthens community resilience.


---


## Background

* The [opioid crisis](https://www.cdc.gov/overdose-prevention/about/index.html) remains one of the most devastating public health emergencies in the United States, claiming over [80,000](https://www.cdc.gov/overdose-prevention/about/understanding-the-opioid-overdose-epidemic.html) lives in 2022 alone. 

* Fentanyl, the illegally-made synthetic opioid, is responsible for [90%](https://www.cdc.gov/overdose-prevention/about/index.html?utm_) of all opioid deaths, and [68%](https://www.cdc.gov/overdose-prevention/about/index.html?utm_) of all overdose deaths.

* [Precursors for fentanyl production](https://www.brookings.edu/articles/the-fentanyl-pipeline-and-chinas-role-in-the-us-opioid-crisis/?utm_) are produced in China and shipped to Mexico, where they are made into fentanyl and distributed by cartels. According to the BBC, this route is how [98%](https://www.bbc.com/news/articles/cvg93nn1e6go?utm_) of all fentanyl makes it into the US.

* In 2023, [over 25,000 pounds](https://www.bbc.com/news/articles/cvg93nn1e6go?utm_) of fentanyl was seized at the US-Mexico border. The [lethal dose](https://www.bbc.com/news/articles/cvg93nn1e6go?utm_) of fentanyl can be as low as 2mg.
  
  - **The [lethal dose](https://www.bbc.com/news/articles/cvg93nn1e6go?utm_) = as low as 2 mg**
  - **Total fentanyl seized at border in 2023 = 25,000lbs --> 11,339,809,250 mg**
  - **Potential lethal doses = 5,669,904,625 people**

    > ⚠️ Theoretically, that’s enough to kill over **5.6 billion people** — more than 16 times the entire U.S. population.


  
* Localized spikes in overdose rates, often triggered by sudden surges in fentanyl-laced substances, frequently go undetected until it’s too late. 

* Many small towns and under-resourced communities lack real-time surveillance tools or predictive models.

* As a result, public health teams are often left reacting to crises rather than preventing them. To enhance prevention capabilities, public health teams need better foresight to deploy resources early.
  
* I’m personally motivated by witnessing how hard-hit rural areas are affected by the opioid crisis.

---


<p align="center">
  <img src="Opioid%20CDC.png" alt="Opioid overdose trends" width="700">
</p>

<p align="center"><sub>
  <strong>Description:</strong> A line chart depicting three distinct waves of opioid overdose deaths in the U.S. from 1999 to 2019.<br>
  <strong>Source:</strong> CDC – <a href="https://www.cdc.gov/overdose-prevention/about/understanding-the-opioid-overdose-epidemic.html">Understanding the Opioid Overdose Epidemic</a><br>
  <strong>License:</strong> Public Domain (U.S. Government Work)<br>
  <strong>Attribution:</strong> Image courtesy of the Centers for Disease Control and Prevention (CDC)
</sub></p>

---


## How is it used?

Public health workers and local outreach organizations use the dashboard to:

* Monitor overdose trends by ZIP code or county

* Get alerts for statistically unusual spikes

* Prioritize locations for distributing naloxone, educational outreach, and support services

* The dashboard runs weekly on fresh datasets and generates a risk heatmap


Individual users use the dashboard to:

* Receive local alerts
* Locate the nearest rehabilitation centers and naloxone distribution
* See which dates mobile clinics will be in their area
* Find additional local support resources
* Share their story, reach out for help, or ask questions using the anonymous blog
* Identify local organizations who are currently in need of volunteers

---

<p align="center">
  <img src="Opioid%20Risk%20Radar%20Infographic.png" alt="Opioid Risk Radar Infographic" width="1100">
</p>

<p align="center"><sub><em>Infographic created by the author using Canva.</em></sub></p>

---


## Data Sources

* [CDC Overdose Data](https://www.cdc.gov/drugoverdose/data/index.html)
* [CDC Opioid Prescription Data](https://www.cdc.gov/overdose-prevention/data-research/facts-stats/opioid-dispensing-rate-maps.html)
* Local emergency services datasets (911 dispatch, EMS logs, if available)
  
---


## Methods


| Method | Description |
| ----------- | ----------- |
| Logistic Regression | Predicts overdose risk by ZIP code or county using supervised learning. Implemented in Python with scikit-learn. |
| K-means Clustering | Detects emerging geographical overdose hotspots by grouping areas with similar risk patterns. |
| NLP  | Future addition to analyze real-time trends from social media or local news using spaCy or transformer-based models. |
| Data Preprocessing | Performed using Python libraries such as pandas, NumPy, and scikit-learn to clean and engineer features from public health and emergency datasets. |
| Interactive Dashboard   | A prototype will be built using Streamlit or Plotly Dash to visualize risk levels and provide alerts. |
| Geospatial Mapping | Risk heatmaps and clustering results will be displayed using libraries like Plotly or Folium. |
| Automation | Weekly ingestion of public datasets will be automated via APIs or batch uploads. |



---


## Example Code Sninppet

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression

# Load and filter data
df = pd.read_csv("opioid_prescriptions.csv")
df = df[df['Opioid_Prescribed'] == True]

# Feature engineering
df['Prescription_Count'] = df.groupby('ZIP')['Prescription_ID'].transform('count')

# Modeling overdose risk
X = df[['Prescription_Count', 'Previous_Overdoses', 'Population_Density']]
y = df['Overdose_Flag']
model = LogisticRegression().fit(X, y)
```


---


## Challenges

* County-level data lacks fine granularity; neighborhood data may be unavailable

* Data reporting lags can reduce prediction timeliness

* Ethical concerns: must avoid reinforcing bias or stigmatizing areas

* Not meant to predict individual overdose risk — only community-level trends

* Prevent misuse of the data for punitive or discriminatory policies

* Uphold data privacy

---


## What next?

* Partner with a local health department to pilot the dashboard

* Add social media/text analysis using NLP for real-time signals

* Deploy mobile-friendly version for community use

* Incorporate feedback tools for on-the-ground teams to annotate hotspot relevance

---
  

## Acknowledgments

* Project initiation inspired by [Elements of AI course](https://buildingai.elementsofai.com/), presented by the [University of Helsinki and Open University](https://www.helsinki.fi/en/admissions-and-education/open-university/multidisciplinary-themed-modules/artificial-intelligence-collection)
  
* Project concept inspired by state-level opioid dashboards, such as the ["Dose of Reality" Opioid Dashboard from the Washington State Department of Health Services](https://www.dhs.wisconsin.gov/opioids/dashboards.htm)

* Data from [CDC](https://www.cdc.gov/overdose-prevention/about/understanding-the-opioid-overdose-epidemic.html), used under public data guidelines

* Images created using [Canva](https://www.canva.com/)



