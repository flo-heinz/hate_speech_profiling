# Hate Speech Profiling on Reddit

This repository provides tools and data for analyzing hate speech on Reddit. It includes data collection, preprocessing, and machine learning workflows to classify and analyze online discourse.

## Repository Structure


### Key Components

#### `data/`
- **Description**: Contains sample JSON files representing Reddit data. 
- **Structure**:
  - Posts: Title, unique ID, author, timestamp, etc.
  - Comments: Nested comment structure with metadata.

#### `Ethos_Dataset_Binary.csv`
- **Source**: ETHOS hate speech dataset.
- **Details**:
  - Each entry has a numerical score ranging from `0` to `1`.
  - **Score Meaning**:
    - Scores closer to `1` indicate higher likelihood of hate speech.
    - Scores closer to `0` indicate non-hate speech.
  - Binary classification is determined using a threshold (e.g., `0.5`).
- **Purpose**: Used for training and testing machine learning models.

#### `data_processing.ipynb`
- **Purpose**: Performs data preprocessing, model training, and analysis.
- **Features**:
  - **Hate Speech Distribution**: Visualizes the dataset distribution via a pie chart.
  - **Models Implemented**:
    - Naive Bayes + Bi-Gram
    - Logistic Regression + TF-IDF
    - SVM + n-Gram
    - Random Forest + TF-IDF
    - LSTM + TF-IDF
    - CNN + TF-IDF
    - DistilBERT
    - GPT-2
    - LLAMA 2
  - **Performance Metrics**: Compares models using weighted F1-scores.
  - **Subreddit Insights**: Barplots of hate speech instances per subreddit.
  - **User Analysis**: Identifies top contributors of hate speech.

#### `get_data_reddit.ipynb`
- **Purpose**: Collects and preprocesses Reddit data.
- **Features**:
  - Targets specific subreddits.
  - Cleans raw data (removes markdown, spoilers, hashtags, etc.).
  - Outputs structured and clean JSON files for analysis.

## How to Use

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/hate-speech-profiling.git
   cd hate-speech-profiling
