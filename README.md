# RssFeedCrawlerFromUrl-s
Usage
Download main.py and requirements.txt into a folder. Preferably, create a new folder for this purpose.
Install the required packages by running pip install -r requirements.txt.
Create a rss_urls.txt file and enter the RSS feed URLs you want to crawl. Each URL should be on a new line.
Run python main.py to start the crawler, or create a cron job to run it periodically.
Output
The crawler will create a data folder and store the crawled data in it. Articles are grouped by publication date and stored in files named YYYY-MM-DD.pkl.

The .pkl files can be loaded as follows:

import os
import pickle

articles = {}

for file in os.listdir('data/articles'):
    with open(os.path.join('data/articles', file), 'rb') as f:
        articles[file.replace('.pkl', '')] = pickle.load(f)
Each entry in the articles dict uses the following format:

'YYYY-MM-DD': [
    {
        'url': 'example.com/articles/1',
        'title': 'Lorem ipsum dolor sit amet',
        'body': 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
    },
    {
        'url': 'example.com/articles/2',
        'title': 'Lorem ipsum dolor sit amet',
        'body': 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
    }
    # ...
]
