# news_recommendation_system

## Problem Statement

At **iPrint**, an emerging media house in India, we offer media and information services spanning various domains, from sports and weather to healthcare and stocks. Through our online platform, we have consistently delivered timely news to the masses. However, as technology advanced, we faced increasing competition.

In the past, our strategy was to recommend popular news or articles similar to what users previously read. This often led to irrelevant suggestions. As a result, we started losing users and revenue.

To address this decline, we are aiming to personalize user preferences. Our goal is to introduce fresh content daily and assess its impact through user clicks. Furthermore, if a user clicks on a news item, we'll recommend similar articles at the end of the clicked article. This strategy will help us deduce user interests.

I've been tasked as the data scientist to support iPrint in realizing this vision. Using my acquired skills, I am to develop a system that suggests pertinent news articles based on user search history and preferences.

Our objectives are:

1. Recommend the top 10 new articles for users daily.
2. Suggest 10 similar articles based on user clicks.

We need to ensure the system:
- Doesn't recommend removed or previously viewed articles.
- Considers only English articles for content-based recommendations.
- Outputs article names and their IDs.

**Dataset:** The dataset can be accessed from the dataset folder

## Data Dictionary:

1. **consumer_transactions:** This dataset captures our customer interactions.
    - `event_timestamp`: When the user interacted with articles.
    - `interaction_type`: Types include content_commented_on, content_followed, etc.
    - `item_id`: ID of the interacted item.
    - `consumer_id`: ID of the interacting consumer.
    - ... (continue for other fields)

2. **platform_content:** Contains details of our platform's news articles.
    - `event_timestamp`: Interaction time.
    - `interaction_type`: Type of interaction.
    - `item_id`: Article ID.
    - `producer_id`: ID of the article's producer.
    - ... (continue for other fields)

## Procedure:

### Data Pre-processing:
1. We need to impute ratings based on `interaction type` to derive a `ratings` feature.
2. Filter out English articles from `platform_content`.

### Exploratory Data Analysis:
1. Examine feature distributions and infer insights.
2. Study the frequency of interaction types, consumer locations, item types, etc.

### Recommendation Techniques:
I'll utilize `consumer_interaction` for collaborative filtering models and `platform_content` for content-based recommendations.

#### User-based Collaborative Filtering:
1. Construct a user-item matrix from ratings.
2. Establish a user similarity matrix.
3. Predict user-item ratings.

#### Item-based Collaborative Filtering:
1. Create an item similarity matrix.
2. Recommend the top 10 relevant items based on similarity.

#### Content-based Filtering:
1. Analyze the `keywords` feature through text processing.
2. Suggest articles based on TF-IDF scores.

#### Alternating Least Squares (ALS):
1. Generate Compressed Sparse user-item matrices.
2. Train the ALS model, tweaking its parameters for optimization.

#### Hybrid Systems:
1. Combine normalized scores from different models.
2. Experiment with various hybrid combinations, like Content+Item-based, ALS+Content-based, etc.

### Model Evaluation:
- Use RMSE, MAE, and precision@k for specific user recommendations.
- Employ global precision@k for overall system assessment.

Furthermore, I'm exploring other online evaluation methods, especially for the second part of the problem statement. I'm excited to explore new techniques beyond those discussed in our previous module.
