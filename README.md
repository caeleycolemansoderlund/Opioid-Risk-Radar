
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

The platform is built for dual use: public health agencies and outreach organizations can use it to monitor trends, identify rising-risk areas, and strategically deploy resources like naloxone, mobile clinics, and educational outreach. At the same time, individual users can access localized alerts, find nearby support services, and connect with others through anonymous tools. The goal is for Opioid Risk Radar to act as both a tool for early intervention, as well as support community resilience.


---


## Background

The [opioid crisis](https://www.cdc.gov/overdose-prevention/about/index.html) continues to take thousands of lives annually. Despite existing efforts, localized spikes in overdoses often go unnoticed until it’s too late. Many communities lack tools to proactively detect and respond to growing risk areas.

* Over [80,000](https://www.cdc.gov/overdose-prevention/about/understanding-the-opioid-overdose-epidemic.html) opioid overdose deaths in the US in 2022
* Small towns and under-resourced communities lack predictive tools
* Public health teams need better foresight to deploy resources early
* I’m personally motivated by witnessing how hard-hit rural areas are affected by the opioid crisis

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
| Logistic Regression | Predicts overdose risk by area |
| K-means Clustering | Identifies emergent geographical overdose hotspots |
| NLP (future) | For analyzing trends in local text data or social media |
| Data Preprocessing | Handled with Python, using pandas, scikit-learn, and NumPy |


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

---


## What next?

* Partner with a local health department to pilot the dashboard

* Add social media/text analysis using NLP for real-time signals

* Deploy mobile-friendly version for community use

* Incorporate feedback tools for on-the-ground teams to annotate hotspot relevance

---
  

## Acknowledgments

* Inspired by state-level opioid dashboards, such as the ["Dose of Reality" Opioid Dashboard from the Washington State Department of Health Services](https://www.dhs.wisconsin.gov/opioids/dashboards.htm)

* Data from [CDC](https://www.cdc.gov/overdose-prevention/about/understanding-the-opioid-overdose-epidemic.html), used under public data guidelines

* Concept inspired by [Elements of AI course](https://buildingai.elementsofai.com/), presented by the [University of Helsinki and Open University](https://www.helsinki.fi/en/admissions-and-education/open-university/multidisciplinary-themed-modules/artificial-intelligence-collection)

