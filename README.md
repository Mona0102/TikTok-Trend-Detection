# TikTok-Trend-Detection

### Business Objective
The client is a leading company in developing consumer products for the home. Its product development process is initiated by various factors such as retail partners, industry trends, competitors’ actions, information from teams and factories, social media buzz, reviews, and google trends. Currently, its internal data analytics system is only gathering data from Amazon (rankings, reviews). Its analytics team does research online with known keywords and uses that information to decide whether a product is or will be a trend. They then pitch the idea to a retail partner and move forward.

The client is now looking into building an engine that utilizes social media data to identify trends in its product categories and related content in the industry automatically. The engine will unveil product trends on social media and speed up the overall new product development process, creating competitive advantages and innovative opportunities for its business endeavors.

### Project Objectives
Create a pipeline/process to source and analyze social media data and predict the future trend of kitchenware and/or household products.
- Use API to collect social media data.
- Use programming languages, preferably Python, to clean and analyze possible trends. 
- Identify trendy products before the peak of the trend.

### Outcomes
Mona led a team of 5 students and collectively built a pipeline that collects TikTok data through API and audio recognition python packages, cleanses and transforms text data with NLP techniques, and detects trends through time series analysis. 

The methodology was deployed to identify social media trends to be included in a dashboard for product managers. Product managers can explore analysis results, extract insights and make new product development decisions backed by social listening data. This analysis showcases viral or potential trends and is crucial for the client company's negotiation with partner vendors.

### Key Assumptions
1. We will still be able to collect text data from TikTok using API in the future. 
2. Our pipeline will be effective as long as we have the data needed.
3. Trends within 6-month period are most useful for identifying trends.
4. The market is mainly in North America where most customers speak English.

### Data Source and API
The project uses an exsiting API called TikTok Scraper API on Rapid API.
(https://rapidapi.com/JoTucker/api/tiktok-scraper2/)
Because of the time restraint of the project, we decided to go with existing APIs instead of building our own scraper. We analyzed potential data sources including the official APIs of Facebook, Instagram, and Twitter and concluded that these official APIs provided limited data. Besides, data collected from these platforms contained a lot of robot-generated or irrelavant information.

We also considered social media platform TikTok because of its increasing popularity. Its abundance of genuine user-generated content produces valuable trends businesses don't want to miss out on.

The client's IT department pointed us to an API website that they had been using and we discovered TikTok Scraper API by JoTucker. This API returns:
- Video caption, id, timestamp, and url
- Comment text, id, the id of the video it belongs, timestamp
- Comments and likes count  
After purchasing the Mega plan, we were able to request sufficient and useful data for our project.

### NLP (Natural Language Processing)


### Code Files
The functions of the 5 code files in the Code folder are described in the respective titles. Codes are commented in detail and organized in blocks.

### User Guide
The User Guide in the Code folder provides more details about the code and how the IT department can use it.
