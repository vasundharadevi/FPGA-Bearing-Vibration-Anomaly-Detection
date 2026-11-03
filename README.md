# FPGA-Bearing-Vibration-Anomaly-Detection
FPGA-based bearing vibration anomaly detection using Python, Verilog, and NASA IMS data

## Project Overview
This project explores the development of an FPGA-based bearing vibration anomaly detection system using the NASA IMS Bearing Dataset.
The objective is to analyze vibration measurements, extract meaningful signal features, and identify unusual vibration patterns using a threshold-based detection algorithm.
Python is used for dataset preprocessing and signal analysis, while Verilog will be used to implement the digital hardware architecture.
The project is being developed and verified through simulation without requiring a physical FPGA board.

## Dataset

* Dataset: NASA IMS Bearing Dataset
* Source: [Kaggle – Bearing Dataset](https://www.kaggle.com/datasets/vinayak123tyagi/bearing-dataset)
* Number of channels in the selected measurement: 8
* Samples per measurement snapshot: 20,480
* Selected signal: Channel 1

## Current Implementation

### 1. Dataset Processing

* Downloaded the dataset using KaggleHub in Google Colab.
* Inspected the dataset structure and measurement files.
* Loaded vibration measurements using Pandas.

### 2. Signal Analysis

* Extracted Channel 1 vibration measurements.
* Visualized the raw vibration waveform.
* Divided the signal into non-overlapping windows of 256 samples.

### 3. Feature Extraction

Calculated Mean Absolute Value (MAV):

MAV = (1/N) × Σ |x[i]|

* Generated 80 MAV values per measurement snapshot.
* Extended the analysis to 20 measurement snapshots.
* Generated a total of 1,600 MAV values.

### 4. Statistical Analysis

Calculated:

* Mean MAV
* Standard deviation
* Minimum and maximum MAV
* MAV distribution

### 5. Provisional Anomaly Detection

Used a statistical threshold:

Threshold = Mean + 3 × Standard Deviation

Results from the selected 20 snapshots:

* Baseline mean: 0.1048806372
* Baseline standard deviation: 0.0072325984
* Provisional threshold: 0.1265784325
* Windows exceeding threshold: 5
* Total windows analyzed: 1,600
* Percentage exceeding threshold: 0.3125%

These are preliminary threshold exceedances and are not confirmed bearing fault labels.

## Technology Stack

* Python
* NumPy
* Pandas
* Matplotlib
* Google Colab
* Verilog (planned)
* Icarus Verilog (planned)
* GTKWave (planned)
* Yosys (planned)

## Planned Hardware Implementation

The next development stages will include:

1. Fixed-point representation of vibration samples.
2. Verilog implementation of absolute-value logic.
3. 256-sample accumulation.
4. MAV calculation.
5. Threshold comparison.
6. Verilog testbench development.
7. RTL simulation and verification against Python results.

## Project Status

* [x] Dataset acquisition and inspection
* [x] Raw vibration signal visualization
* [x] MAV feature extraction
* [x] Analysis of 20 measurement snapshots
* [x] Statistical threshold calculation
* [x] Preliminary threshold-exceedance detection
* [ ] Snapshot-level trend analysis
* [ ] Fixed-point conversion
* [ ] Verilog RTL implementation
* [ ] Testbench development
* [ ] RTL simulation and verification

## Note
The current threshold is exploration. Additional analysis and validation are required before interpreting threshold spikes as actual bearing faults.

