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
- **Purpose**: Executes classification workflows and visualizes the ETHOS dataset.
- **Key Features**:
  - **Hate Speech Distribution**: Displays a pie chart of the hate speech vs. non-hate speech distribution in the ETHOS dataset.
  - **Classification Models**: Implements and evaluates a variety of models, including:
    - Naive Bayes + Bi-Gram
    - DistilBERT
    - Logistic Regression with TF-IDF
    - GPT-2
    - LLAMA 2
    - LSTM with TF-IDF
    - CNN with TF-IDF
    - SVM with n-Gram
    - Random Forest with TF-IDF
  - **Performance Comparison**: Barplot comparing weighted F1-scores of all classifiers to identify the best-performing model.
  - **Subreddit Analysis**: Barplot showcasing the number of hate speech instances per subreddit.
  - **User Analysis**: Creates a table of top users contributing to hate speech.

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
