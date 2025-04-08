Sentiment Analysis using Google Generative AI
=============================================

This repository contains code to perform sentiment analysis on text data using the Google Generative AI API. The code processes text data, adds sentiment analysis results, and generates a sentiment distribution graph.

## Installation

1. Install the required Python packages using `pip`:

   ```bash
   $ pip install google-generativeai
   $ pip install json
   $ pip install pandas
   $ pip install matplotlib
   $ pip install time
   $ pip install dotenv


2. Create a .env file in the root directory and add your Google Generative AI API key as follows:
    ```
    API_KEY=your_api_key_here
    ```
    ### Load API_KEY from .env file
    ```
    load_dotenv()
    ```
## How it works

1. Google Generative AI Palm API Key
    ```
    palm.configure(api_key=os.environ['API_KEY'])
    ```

2. Google Generative AI Default Settings
    ```
    defaults = {
        # ... (default settings)
    }
    ```

3. Process each record
    ```
    def process_and_append_added_sentiment_and_score_results_to_csv(single_record):
        # ... (processing logic)
    ```    

4. Generate sentiment analysis results and save them to a CSV file.

    4.1 Read the data into a DataFrame
    ```
    df_no_sentiment_no_score = pd.read_csv("food_review_data_no_sentiment_no_score.csv")
    df_no_sentiment_no_score_filtered = df_no_sentiment_no_score[['Id', 'Summary']]
    ```

    4.2 Set the chunk size (Do Not Change)
    ``` 
    chunk_size = 1 
    ```
    4.3 Iterate over chunks
    ``` 
    for i in range(0, len(df_no_sentiment_no_score_filtered), chunk_size):
        chunk = df_no_sentiment_no_score_filtered.iloc[i:i+chunk_size]
        # Save Added Sentiment and Score Results to a CSV file
        process_and_append_added_sentiment_and_score_results_to_csv(chunk)
        # Wait for 5 seconds To Avoid Hitting API Quota
        time.sleep(5)
    ```     

## Generates Sentiment Distribution Graph

    ``` 
    def create_sentiment_distribution_graph():
        # ... (graph generation logic)

    create_sentiment_distribution_graph()
    ``` 




