Twitter Scraping Tool
A tool that allows users to scrape tweets from Twitter using snscrape and store them in MongoDB for further analysis. The tool also provides a GUI built with Streamlit for easy access to the scraped data.

Prerequisites
Python 3.x
snscrape
pandas
pymongo
streamlit
Installation
First, ensure that you have Python 3.x installed on your machine.

Install the required packages by running the following command:

Copy code
pip install snscrape pandas pymongo streamlit
Clone the repository and navigate to the project directory.
Twitter Scraping using snscrape
To scrape tweets, you will need to run the script scrape_tweets.py from the command line and provide the following inputs:

Twitter username, hashtag or keywords: You will need to provide the username, hashtag or keywords for which you want to collect tweets.
Number of tweets: The number of tweets you want to collect.
The tweets will be saved in json format in the data folder with the name scraped_tweets.json

Note: The tool uses twitter search API, thus it will only provide tweets from the last 7 days. Also, twitter API has a rate limit, so you may need to wait for some time before running the script again.

Creating a Dataframe with Scraped Data
Run the script create_dataframe.py to convert the scraped tweets into a dataframe.

The dataframe will be saved in the data folder with the name scraped_tweets.csv

Storing Data in MongoDB
Make sure that you have MongoDB installed and running on your machine.

Run the script store_data.py to store the dataframe into MongoDB.

The data will be stored in the twitter collection of the twitterdb database.

Creating a GUI using Streamlit
Run the script gui.py to launch the GUI.

The GUI allows users to interact with the data stored in MongoDB and search for tweets by username, hashtag or keywords.

Use the dropdown menus to select the desired options and press Search.

Conclusion
The tool allows users to scrape tweets from Twitter using snscrape and store them in MongoDB for further analysis. The tool also provides a GUI built with Streamlit for easy access to the scraped data.

Please let me know if you have any questions or need further clarification.

Please note that this is just a sample README file and you may need to adjust it to your specific project.




