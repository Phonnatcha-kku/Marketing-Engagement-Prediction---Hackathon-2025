+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ad_campaign_db.sqlite
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
The ad_campaign_db.sqlite is a single-file, serverless database that contains a comprehensive, synthetic dataset for analyzing social media advertising performance.

The database is structured around a relational schema with four interconnected tables. This design allows for complex queries to join campaign information with user behavior, simulating a real-world marketing analytics environment.

users: This table contains individual user profiles. The data is entirely synthetic and free of PII (Personally Identifiable Information). Key columns include a unique user_id, demographic data like user_age and user_gender, and geographic information such as country and location. This table is the foundation for audience segmentation.

campaigns: This table stores high-level strategic information for each ad campaign. It includes key metrics such as campaign_id, a total_budget, and duration_days. This provides the business context for the performance data.

ads: This table represents the individual ad creatives. Each ad is linked to a specific campaign via a campaign_id and contains its own targeting parameters, including target_gender, target_age_group, and target_interests. This is crucial for evaluating the effectiveness of different ad strategies.

ad_events: This is the central transactional log of the database. It records every interaction a user has with an ad. Each event is tied to a specific ad and user through foreign keys (ad_id and user_id). The table captures the timestamp, day_of_week, time_of_day, and the event_type (e.g., 'Impression', 'Click', 'Purchase'), providing a complete picture of the user's journey.
===============================================================================================


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ad_events.csv
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This is the most critical and granular file in the dataset, serving as the central log of all user interactions. Each row in ad_events.csv represents a single user interaction, from a simple viewing to a final purchase. The data links a specific ad_id and user_id for each event, providing a complete picture of the user's journey. Key columns include a precise timestamp, a derived day_of_week and time_of_day for time-based analysis, and the event_type itself ('Impression', 'Click', 'Purchase', etc.). This file is the primary resource for building an ad funnel, calculating conversion rates, and performing in-depth behavioral analysis.
===============================================================================================


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ads.csv
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This file details the individual ad creatives that were part of the campaigns. Each row in ads.csv is a specific ad, linked to its parent campaign via a campaign_id foreign key. The file provides insight into the ad's configuration, including the ad_platform it ran on, its ad_type (e.g., 'Video', 'Image'), and its specific targeting parameters. These parameters include target_gender, target_age_group, and a list of target_interests. Analyzing this data allows you to test hypotheses about which ad creative types and targeting strategies are most effective.
===============================================================================================


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
campaigns.csv
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This file serves as the strategic backbone of the dataset, providing high-level information for each marketing campaign. Each row represents a single campaign, defined by a unique campaign_id. The data includes a campaign name, its start_date and end_date, and a pre-calculated duration_days to simplify time-based analysis. The total_budget for each campaign is also listed, which is essential for calculating cost-related metrics like ROI and cost per acquisition. This file allows for a top-down analysis of the campaign portfolio and its overall performance.
===============================================================================================


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
users.csv
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This file contains the individual profiles for every user in the synthetic dataset. Each row in users.csv represents a single, unique user, complete with demographic and geographic information. The data is entirely synthetic and was generated using realistic, weighted distributions to mimic real-world population demographics without any PII (Personally Identifiable Information). Key attributes for each user include a unique user_id, their user_gender and user_age, an analytically convenient age_group, and their country and location. This file is a foundational table for performing market segmentation, cohort analysis, and understanding how different audience demographics respond to ad campaigns.
===============================================================================================