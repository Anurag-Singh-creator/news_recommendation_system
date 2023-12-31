# news_recommendation_system

## Problem Statement

**iPrint**, an emerging media house in India, offer media and information services spanning various domains, from sports and weather to healthcare and stocks. Through our online platform, the company has consistently delivered timely news to the masses. However, as technology advanced, the company faced increasing competition.

In the past, the strategy was to recommend popular news or articles similar to what users previously read. This often led to irrelevant suggestions. As a result, the company started losing users and revenue.

To address this decline, company is aiming to personalize user preferences. The goal is to introduce fresh content daily and assess its impact through user clicks. Furthermore, if a user clicks on a news item, then recommend similar articles at the end of the clicked article. This strategy will help us deduce user interests.

The aim here is to develop a system that suggests pertinent news articles based on user search history and preferences.

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
    - `event_timestamp`: Timestamp at which the user interacted with the news articles.
    - `interaction_type`: Type of interaction made by the user. Types include content_commented_on, content_followed, content_liked, content_saved, content_watched.
    - `item_id`: ID of the item with which the user interacted.
    - `consumer_id`: ID of the consumer who interacted with the item.
    - `consumer_session_id`: ID of the session during which the user interacted with the item.
    - `consumer_device_info`: Information about the device used by the consumer.
    - `consumer_location`: Location of the consumer.
    - `country`: Country of the consumer.

2. **platform_content:** Contains details of our platform's news articles.
    - `event_timestamp`: Timestamp at which the interaction happened.
    - `interaction_type`: Type of the interaction - content present/pulled out.
    - `item_id`: ID of the item on the platform.
    - `producer_id`: ID of the producer.
    - `producer_session_id`: ID of the session when the producer interacted with the item.
    - `producer_device_info`: Information about the device used by the producer.
    - `producer_location`: Location of the producer.
    - `producer_country`: Country of the producer.
    - `item_type`: Type of item on the platform, such as HTML, VIDEO, RICH.
    - `item_url`: URL of the item.
    - `title`: Title of the content.
    - `text_description`: Description of the content.
    - `language`: Language of the content on the platform.


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
