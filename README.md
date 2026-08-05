Bearing Blueprints

Interactive visualization of bearing degradation from detection to prognosis

Bearing Blueprints is an interactive visual analytics project developed for DTSA 5304 Fundamentals of Data Visualization and is intender for educational purposes only.

The project uses the NASA IMS Bearing Dataset, Experiment 2, to explore how visualization can support predictive maintenance tasks. Four bearings were monitored during a run-to-failure experiment using vibration measurements collected over time.

The application is designed to help users:

* detect progressive degradation;
* identify which bearing requires attention first;
* inspect the evidence supporting an anomaly;
* compare healthy and degraded vibration behaviour;
* explore how degradation trends may support an estimation of future failure.

Live Visualization

* Open the interactive project

Project Structure

The project contains two complementary visualizations.

Operational Monitoring

The operational dashboard supports detection, diagnosis, and maintenance prioritization through an overview-to-detail workflow.

Users can move from:

Fleet overview
    ↓
Bearing condition
    ↓
Recording inspection
    ↓
Signal windows
    ↓
Raw vibration comparison

Prognostic Exploration

The prognostic visualization explores how different degradation models project the observed trend toward failure.

This section compares:

* multiple growth laws;
* different decision times;
* projected and actual failure times;
* prediction error;
* warning time;
* uncertainty across model choices.

The prognostic results are exploratory and should not be interpreted as validated operational predictions.

Research Questions

The project investigates the following questions:

1. Can an interactive visualization help users distinguish normal bearing behaviour from progressive degradation?
2. Can users identify when persistent degradation begins and determine which bearing requires maintenance attention first?
3. Does providing multiple levels of visual evidence help users understand why a condition is considered anomalous?
4. Once degradation becomes persistent, can the observed trends support an exploratory estimation of remaining useful life while communicating prediction uncertainty?

Dataset

The project uses the publicly available NASA IMS Bearing Dataset:

* NASA IMS Bearings Dataset

Experiment 2 contains vibration recordings from four bearings operating under controlled load and speed conditions until the end of the test.

Repository Structure

bearing-blueprints/
├── index.html
├── operational.html
├── prognostic.html
├── README.md
├── report/
│   └── project-report.pdf
└── images/
    ├── bearing.webp
    ├── operational-overview.png
    ├── operational-detail.png
    └── prognostic-overview.png

Technologies

* Python
* Altair
* Vega-Lite
* HTML
* CSS
* JavaScript
* GitHub Pages

Evaluation

The visualization was evaluated with three railway professionals:

* one railway mechanical engineer involved in the design of point machines in Katowice, Poland;
* two railway maintenance engineers based in Florence, Italy.

The evaluation focused on interpretability, usability, degradation detection, maintenance prioritization, and confidence in the displayed evidence.

Limitations

This project is based on a single run-to-failure experiment containing four bearings. The prognostic analysis is exploratory and is not intended to establish general prognostic accuracy.

Future work may include:

* evaluation with a larger group of industrial users;
* application to additional predictive maintenance datasets;
* improved uncertainty visualization;
* comparison with alternative health indicators;
* validation of prognostic models across multiple failure scenarios.

Course

Final project for:

Information Visualization
MS in Data Science
University of Colorado Boulder

Author

Eduardo Di Santi

License

This repository is intended for academic and educational use.

The NASA IMS Bearing Dataset remains subject to the terms of its original provider. External images and referenced materials remain the property of their respective owners.
