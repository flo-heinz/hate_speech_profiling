# Hate Speech Profiling on Reddit

This repository contains the data and code used for detecting and analyzing hate speech on Reddit. It integrates data collection, preprocessing, and classification workflows for effective hate speech detection using machine learning and NLP techniques.

## Repository Structure


### 1. `data/`
- **Description**: This folder contains sample JSON files representing the structure of Reddit data collected for analysis.
- **Structure of JSON files**:
  - `Post information`: Includes title, unique ID, URL, author, score, comment count, and timestamp.
  - `Comment details`: Nested structure for comments with fields such as comment body, score, and timestamp.

### 2. `Ethos_Dataset_Binary.csv`
- **Description**: A binary-labeled dataset sourced from the ETHOS hate speech detection project.
- **Classes**:
  - Hate Speech
  - Non-Hate Speech
- **Purpose**: Serves as the primary training and evaluation dataset for the classification models.

### 3. `data_processing.ipynb`
- **Purpose**: Executes the classification workflows and visualizes the dataset distribution.
- **Key Features**:
  - Loads and preprocesses data from the ETHOS dataset or JSON files.
  - Implements various machine learning classifiers, including:
    - Naive Bayes
    - Support Vector Machines (SVM)
    - Logistic Regression
    - Deep Learning models (e.g., DistilBERT, LSTM)
  - Displays the distribution of hate speech vs. non-hate speech instances in the ETHOS dataset.
  - Evaluates models using metrics such as weighted F1-scores.

### 4. `get_data_reddit.ipynb`
- **Purpose**: Scrapes Reddit posts and comments and preprocesses them for analysis.
- **Key Features**:
  - Targets specific subreddits known for polarizing content.
  - Collects data in a structured JSON format.
  - Cleans and preprocesses data during collection by:
    - Removing markdown formatting, hashtags, and spoilers.
    - Organizing comments and metadata in a ready-to-use format.
  - Outputs cleaned JSON files directly for further processing.

## Usage Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/hate-speech-profiling.git
   cd hate-speech-profiling
