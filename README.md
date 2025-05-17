
<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Opioid Risk Radar

Final project for the Building AI course

## Summary

Opioid Risk Radar is a community-focused AI dashboard that predicts local overdose risks using public health and prescription data. It helps public health officials identify and act on emerging overdose hotspots before they escalate.

## Background

The opioid crisis continues to take thousands of lives annually. Despite existing efforts, localized spikes in overdoses often go unnoticed until it’s too late. Many communities lack tools to proactively detect and respond to growing risk areas.

* Over 80,000 opioid overdose deaths in the US in 2022
* Small towns and under-resourced communities lack predictive tools
* Public health teams need better foresight to deploy resources early
* I’m personally motivated by witnessing how hard-hit rural areas are by the opioid crisis


## How is it used?

Public health workers and local outreach organizations use the dashboard to:

* Monitor overdose trends by ZIP code or county

* Get alerts for statistically unusual spikes

* Prioritize locations for distributing naloxone, educational outreach, and support services

The dashboard runs weekly on fresh datasets and generates a risk heatmap


<img src="Opioid%20Risk%20Radar.png" width="400">


## Data sources and AI methods

Data sources:

* CDC Overdose Data

* Medicare Opioid Prescribing Rates

* Local emergency dispatch (if available)

AI methods:

* Logistic regression for predicting overdose probability

* K-means clustering to detect emerging geographic hotspots

* Data cleaning and feature engineering using Python (pandas, scikit-lea



## Challenges

* County-level data lacks fine granularity; neighborhood data may be unavailable

* Data reporting lags can reduce prediction timeliness

* Ethical concerns: must avoid reinforcing bias or stigmatizing areas

* Not meant to predict individual overdose risk — only community-level trends



## What next?

* Partner with a local health department to pilot the dashboard

* Add social media/text analysis using NLP for real-time signals

* Deploy mobile-friendly version for community use

* Incorporate feedback tools for on-the-ground teams to annotate hotspot relevance

  

## Acknowledgments

* Inspired by state-level opioid dashboards 

* Data from CDC and CMS, used under public data guidelines

* Concept inspired by Elements of AI course 

