Dataset Generation Pipeline

This directory contains the Python modules used to generate all datasets required by the visualizations presented in the Bearing Blueprints project.

The pipeline starts from the original NASA IMS Bearing Dataset and progressively builds higher-level representations used for degradation monitoring and exploratory prognosis.

The scripts are intended to be executed in sequence.

⸻

Processing Pipeline

NASA IMS Dataset
        │
        ▼
ims_io.py
        │
        ▼
shared_model.py
        │
        ▼
calibration.py
        │
        ▼
departure.py
        │
        ├───────────────► Operational Dashboard
        │
        ▼
forecast.py
        │
        ▼
backtest.py
        │
        ▼
Prognostic Visualization

⸻

Script Description

ims_io.py

Loads the original NASA IMS Experiment 2 dataset.

Main responsibilities:

* Load vibration recordings.
* Sort recordings chronologically.
* Parse timestamps.
* Generate fixed-length signal windows.
* Provide the raw data used throughout the pipeline.

⸻

simulator.py

Generates synthetic healthy bearing signals.

These signals are not used for evaluation.

Instead, they are used to train a shared nominal representation that can later be transferred to real assets.

⸻

shared_model.py

Builds and trains the shared convolutional autoencoder.

The model learns the nominal behaviour of healthy bearings using only simulated data.

After training, the same representation is applied to every NASA bearing without retraining.

The reconstruction error becomes the anomaly score used by the remaining stages.

⸻

calibration.py

Estimates the operational threshold for each bearing.

The calibration procedure computes the nominal operational radius from the initial healthy observations.

This threshold is frozen afterwards and represents the reference against which future degradation is measured.

⸻

departure.py

Detects persistent departures from nominal behaviour.

Instead of reacting to isolated anomalies, the algorithm declares degradation only after repeated exceedances of the calibrated threshold.

This produces:

* degradation onset;
* declaration time;
* lead time before failure.

These outputs are used by the operational visualization.

⸻

forecast.py

Explores how degradation evolves after departure has been detected.

Several mathematical growth models are fitted to the observed degradation trajectory and projected into the future.

This module is exploratory and is not part of the validated detection methodology.

Its outputs are used by the prognostic visualization.

⸻

backtest.py

Evaluates the forecasting procedure retrospectively.

For different decision times, each projection is compared with the actual failure observed in the experiment.

The generated datasets include quantities such as:

* projected failure time;
* prediction error;
* warning time;
* model comparison.

These results support the prognostic visualizations but should not be interpreted as a validated Remaining Useful Life estimator.

⸻

config.py

Centralises every experimental parameter used throughout the project.

Examples include:

* signal window length;
* latent dimension;
* calibration parameters;
* persistence rules;
* simulator configuration;
* forecasting settings.

Using a single configuration file guarantees reproducibility across all experiments.

⸻

Generated Datasets

The pipeline produces two groups of datasets.

Operational Monitoring

Used by the operational dashboard.

Includes:

* Health Index evolution
* Persistent departure
* Threshold crossings
* Recording-level statistics
* Window-level anomaly scores

⸻

Prognostic Exploration

Used by the exploratory prognosis dashboard.

Includes:

* fitted degradation models;
* projected trajectories;
* prediction errors;
* warning time;
* comparison between forecasting models.

⸻

Notes

The operational monitoring pipeline reproduces the methodology described in the accompanying technical report.

The forecasting modules (forecast.py and backtest.py) represent an exploratory extension developed exclusively for visualization purposes. They are intended to investigate how different degradation models behave after degradation has already been detected and should not be interpreted as validated prognostic models.