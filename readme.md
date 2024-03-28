# Drug-Malady Classification Dataset Preparation

## Introduction
This project leverages a machine learning model, fine-tuned with OpenAI's GPT-3, for classifying drugs based on their associated maladies. It involves processing a dataset of drugs and their corresponding maladies, preparing the data for model training, and using the model to predict maladies from drug names.

## Design
The project design includes several key steps:
- **Data Preparation**: Starting with an Excel dataset of drugs and maladies, using Python and Pandas for data processing.
- **Data Conversion**: Converting the processed data into JSON Lines (JSONL) format for compatibility with the OpenAI API.
- **Environment Setup**: Establishing a Python virtual environment for dependency management.
- **Model Training with OpenAI**: Fine-tuning a GPT-3 model using the OpenAI API, with the data divided into training and validation sets.
- **Classification and Prediction**: Using the fine-tuned model to classify drugs and predict maladies based on drug names.

## Implementation
To implement this project, the following steps are required:
1. **Set up the Python Environment**:
   ```bash
   python3 -m venv venv
   . venv/bin/activate
   pip install pandas openpyxl openai==0.28

# Process the Dataset

- **Run app.py to process the Excel dataset and create a JSONL file.**

  ```bash
  python3 app.py
  ```

# Prepare Data for Fine-Tuning

- **Use OpenAI CLI for data preparation.**

  ```bash
  openai tools fine_tunes.prepare_data -f drug_malady_data.jsonl
  ```

# Set Up OpenAI API Key

- **Export your OpenAI API key.**

  ```bash
  export OPENAI_API_KEY="your_api_key_here"
  ```

# Fine-Tune the Model

- **Initiate the fine-tuning process with the OpenAI API.**

  ```bash
  openai api fine_tunes.create \
     -t "drug_malady_data_prepared_train.jsonl" \
     -v "drug_malady_data_prepared_valid.jsonl" \
     --compute_classification_metrics \
     --classification_n_classes 7 \
     -m ada \
     --suffix "drug_malady_data"
  ```

# Follow the Fine-Tuning Job

- **Monitor the fine-tuning job with the job ID.**

  ```bash
  openai api fine_tunes.follow -i <JOB ID>
  ```

# Run the Test Script

- **Use test.py for drug classification.**

  ```bash
  python3 test.py
  ```
