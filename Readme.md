# Price-Predict

Predict housing prices using ML pipelines, experiment tracking, and deployment tools.

---

## Overview

**Price-Predict** is a machine learning project focused on predicting housing prices. It leverages modern MLOps tools such as MLflow and ZenML, and provides end-to-end workflows including data processing, model training, experiment tracking, and deployment.

> **Note:** The following description is based on the files available in the root of the repository. There may be additional files or directories not listed due to API result limitations.  
> Explore the full repo here: [Wadu-TT/Price-Predict on GitHub](https://github.com/Wadu-TT/Price-Predict/tree/main/)

---

## Repository Structure

- `analysis/` - Notebooks or scripts for data analysis (details not shown).
- `config.yaml` - Main project configuration, including model metadata and required integrations.
- `data/`, `extracted_data/` - Directories for storing raw and processed data.
- `mlruns/` - MLflow experiment tracking artifacts.
- `pipelines/` - Contains pipeline definitions for training and deployment.
- `requirements.txt` - Python dependencies for running the project.
- `run_deployment.py` - CLI for deploying the trained model as a prediction service.
- `run_pipeline.py` - CLI for running the machine learning pipeline and tracking experiments.
- `sample_predict.py` - Example script for making predictions against the deployed model API.
- `src/`, `steps/` - Source code and modular pipeline steps.

---

## Getting Started

### Prerequisites

- Python 3.8+
- Pip
- (Recommended) Virtual environment tool: `venv` or `conda`

Install dependencies:

```sh
pip install -r requirements.txt
```

### Configuration

The `config.yaml` file defines project settings such as:

```yaml
enable_cache: False

settings:
  docker:
    required_integrations:
      - mlflow

model:
  name: prices_predictor
  license: Apache 2.0
  description: Predictor of housing prices.
  tags: ["regression", "housing", "price_prediction"]
```

---

## Usage

### Running the Training Pipeline

This will execute the ML pipeline and print instructions to launch the MLflow UI for experiment tracking.

```sh
python run_pipeline.py
```

Output (example):

```
Now run 
    mlflow ui --backend-store-uri '<mlflow_tracking_uri>'
To inspect your experiment runs within the mlflow UI.
```

### Deploying the Model

To deploy the trained model as a prediction service:

```sh
python run_deployment.py
```

To stop the prediction service when done:

```sh
python run_deployment.py --stop-service
```

The script will print the local prediction server URL.

---

### Making Predictions

Use the provided `sample_predict.py` script to send sample data for prediction:

```sh
python sample_predict.py
```

This script will POST a sample input to the local MLflow prediction server and print the response.

---

## Example Requirements

The project relies on the following core Python packages (see `requirements.txt` for full list):

- `mlflow`
- `cloudpickle`
- `numpy`
- `pandas`
- `psutil`
- `scikit-learn`
- `scipy`
- `zenml`
- `click`
- `requests`
- `rich`

---

## Experiment Tracking

MLflow is integrated for tracking experiments, models, and deployments.  
Launch the MLflow UI as instructed in the pipeline/deployment scripts to visualize and compare runs.

---

## License

Apache 2.0

---

## Acknowledgements

- Built with [ZenML](https://zenml.io/) for pipeline orchestration and MLOps.
- MLflow for experiment tracking and deployment.

---

*This README was auto-generated based on root-level files. For the most accurate and up-to-date documentation, refer to the repository and code comments.*
