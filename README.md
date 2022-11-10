# TikTok-Trend-Detection (Summer 2022)
Team Members: Yuanying Mo, Fengming Yang, Kodi Leith, Yuhan Tang, Alexis Munguia, Mengying Jin

Instructors: Dr. Jim Hoover, Taikgun Song

## Business Objective
The client is a leading company in developing consumer products for the home. Its product development process is initiated by various factors such as retail partners, industry trends, competitors' actions, information from teams and factories, social media buzz, reviews, and google trends. Currently, its internal data analytics system only gathers data from Amazon (rankings, reviews). Its analytics team does research online with known keywords and uses that information to decide whether a product is or will be a trend. They then pitch the idea to a retail partner and move forward.

The client is now looking into building an engine that utilizes social media data to identify trends in its product categories and related content in the industry automatically. The engine will unveil product trends on social media and speed up the overall new product development process, creating competitive advantages and innovative opportunities for its business endeavors.

## Project Objectives
Create a pipeline/process to source and analyze social media data and predict the future trend of kitchenware and household products.
- Use API to collect social media data.
- Use programming languages, Python, to clean and analyze possible trends. 
- Identify trendy products before the peak of the trend.

## Outcomes
Mona led a team of 5 students and collectively built a pipeline that collects TikTok data through API and audio recognition python packages, cleanses and transforms text data with NLP techniques, and detects trends through time series analysis. 

The methodology was deployed to identify social media trends to be included in a dashboard for product managers. Product managers can explore analysis results, extract insights and make new product development decisions backed by social listening data. This analysis showcases viral or potential trends and is crucial for the client company's negotiation with partner vendors.

## Key Assumptions
1. We will still be able to collect text data from TikTok using API in the future. 
2. Our pipeline will be effective as long as we have the data needed.
3. Trends within a 6-month period are most useful for identifying trends.
4. The market is mainly in North America, where most customers speak English.

## Technical Challenges
### 1. Data Source and Quality
We extracted over 10k videos from 13 hashtags. We also extracted over 300k comments from 13 hashtags.

#### 1.1 API
The project used an existing API called [TikTok Scraper API](https://rapidapi.com/JoTucker/api/tiktok-scraper2/) on Rapid API.
Because of the time restraint of the project, we decided to go with existing APIs instead of building our own scraper. We analyzed potential data sources, including the official APIs of Facebook, Instagram, and Twitter, and concluded that these official APIs provided limited data. Besides, data collected from these platforms contained a lot of robot-generated or irrelevant information.

We also considered the social media platform TikTok because of its increasing popularity. Its abundance of genuine user-generated content produces valuable trends businesses don't want to miss out on.

The client's IT department pointed us to an API website they had been using, and we discovered TikTok Scraper API by JoTucker. This API returns data about [videos](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/1.Get%20Videos%20Multiple%20Hashtags.ipynb) and [comments](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/2.Get%20Comments.ipynb):
- Video caption, id, timestamp, and URL
- Comment text, id, the id of the video it belongs, timestamp
- Comments and likes count

After purchasing the Mega plan, we were able to request sufficient and useful data for our project.

#### 1.2 [Speech Recognition](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/3.Sound%20Recognition%20for%20Videos.ipynb) 
Some video captions don't specify the product mentioned in the video. We transcripted video audio using Python library SpeechRecognition and automated the process with Selenium webdriver and Moviepy. We downloaded each video as a temporary file, ripped audio from the video, ran the Recognizer function in the speech recognition package to transcribe the audio, and saved the text data to the respective row. This step gave us more useful text data for text analysis later on.

### 2. [Data Cleansing and Analyzing](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/4.NLP%2C%20Bigrams%20and%20Colors%20Analysis.ipynb)
After cleaning the video dataset (only keeping videos from 6/2020 to 5/2022 and remove videos with blank transcripts) and the comment dataset using NLP techniques and combining the two datasets, we ended up with a more comprehensive dataset of 249,953 rows. We only kept text data in English because that's the clieint business' primary customers.

#### 2.1 NLP (Natural Language Processing)
##### 2.1.1 Bigram(Ngram) Frequency

Top 20 bigrams in videos:
stainless steel, cutting board, cast iron, salt pepper, non stick, air fryer, ground beef, ice cream, dishwasher safe, drying rack,paper towl, aqua pure, spice rack, ease store, knife set, store gift, meal prep, olive oil, dutch oven, peanut butter.

Top 20 bigrams in comments (after removing non-English words and repeated words):
cinnamon toast, toast crunch, cast iron, cumin powder, stainless steel, salt pepper, cutting board, paper towel, non stick, ice cream, vacuum sealer, game changer, spice rack, wood burning, crunch seasoning, rice dispenser, baking soda, counter tops, air fryer, empty space

##### 2.1.2 Corlor Bigram
Color is one of the most important visual assets of the client's brands. Identifying what colors are trendy is extremely valuable to the client.
We created a function to search top color bigrams. It can also be used to search top bigrams of any word.

#### 2.2 [Time Series (Trend) Analysis](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/5.Trend%20Detection.ipynb)
The team and the client indentified 3 types of trend based on the dataset and business understanding. Below are the criteria for the 3 types of trends.

Type 1 - New Trend
- There is no data before the recent 6 months (before 12/2021)
- There are some data during the recent 6 months (after 12/2021)
- The slope for 2-year data is positive

Type 2 - Peaked Trend
- There is a peak during the recent 6 months (after 12/2021)
We produced a function to return the trendy videos' links where we can further investigate the trend.

Type 3 - Step Change
- There is no peak in the last 6 months (after 12/2021)
- There are some data before the recent 6 months (before 12/2021)
- The slope of the recent 6 months is positive

The code produced lists of bigrams that exhibit these trends.

### [User Guide](https://github.com/Mona0102/TikTok-Trend-Detection/blob/main/Code/User%20Guide%20Analysis%20Using%20TikTok.pdf)
Kodi created a User Guide for the client's IT department to better understand the code.

### Limitations
- The API cannot extract all the videos from one hashtag.
- Mainly used data from one social media platform. 
- Mainly focus on bigrams and color-related bigrams.
- Other criteria for trend detection exist.
- Hard coding issue.

(Updated on 11.10.2022)
