# Twitter Scraping Tool

This project allows you to collect tweets for a specific keyword or hashtag, within a given date range and a limit of tweets to be scraped. The project is built using Python and the popular libraries ***'streamlit', 'pandas', and 'pymongo'***..

## Prerequisites

* Python 3.8 and more

* snscrape

* pandas

* pymongo

* streamlit

* Installation

First, ensure that you have Python 3.x installed on your machine.

Install the required packages by running the following command:

```
pip install snscrape 
pip instal pandas 
pip install pymongo 
pip install streamlit
```
## Workflow

***Scrape tweets:*** The user inputs their desired keyword or hashtag, date range, and tweet limit into the interface created by **streamlit**. The tweets are then scraped using the function module's **twitter_scraper** function which takes in these inputs and uses the **sntwitter** library to scrape tweets from Twitter based on the given keyword or hashtag within the given date range and limited to the given number of tweets.
```
def twitter_scraper(hastag, limit, start_date, end_date):
    tweet_list = []
    for i,tweet in enumerate(sntwitter.TwitterSearchScraper(f'{hastag} since:{start_date} until:{end_date}').get_items()):
        data = [
            tweet.date,
            tweet.user.username,
            tweet.rawContent,
            tweet.lang,
            tweet.viewCount,
            tweet.replyCount,
            tweet.likeCount,
            tweet.retweetCount,
        ]
        tweet_list.append(data)
        if i > limit:
            break
            
    return tweet_list
```

***Create Dataframe:*** The scraped tweets are then converted into a Dataframe using the function **create_dataframe** function. This function takes in the scraped tweets as a list of lists and converts it into a Dataframe using the **pandas** library. The Dataframe contains columns such as 'Date Time', 'Tweet id', 'Tweet Content', 'Username', 'Tweet Language', 'Tweet Views', 'Reply Count', 'like Count', 'Retweet Count'
```
def create_dataframe(tweet_list):
    tweet_data = pd.DataFrame(tweet_list, columns = [
        'Date Time',
        'Username',
        'Tweet Content',
        'Tweet Language',
        'Tweet Views',
        'Reply Count',
        'like Count',
        'Retweet Count',
    ]
                             )
    return tweet_data
```

***Streamlit GUI:*** The scraped dataframe is then displayed in the Streamlit GUI. The GUI contains the feature to enter the keyword or Hashtag to be searched, select the date range and limit the tweet count need to be scraped.

***Upload to MongoDB:*** The user can then upload the Dataframe to a MongoDB database for further analysis. The user can use the interface to click the 'Upload to MongoDB' button. This button invokes the code which exports the Dataframe to a json format and then uses the pymongo library to connect to a MongoDB instance and stores the data into the database.

***Download as CSV:*** The user can also download the Dataframe as a CSV file for easy storage and manipulation. The user can use the interface to click the 'Download as CSV' button. This button invokes the code which exports the Dataframe to a csv format and then uses the base64 library to encode the csv data and then creates a link which can be used to download the csv file

***Download as JSON:*** The user can also download the Dataframe




