---
layout: post
title:  "Data Crawling"
excerpt: "How I used python web crawlers to scrape user comments of naver and daum news"
date:   2020-01-18 09:59:02 +0530
categories: Python Scrapy
---

#### **Motivation**

One of my tasks as an intern was to crawl data from the web. I liked web crawling as the automation aspect to it felt so elegant compared to my other manual tasks but also because the scraping aspect of web crawling was great for practicing coding as parsing required writing lots of loops, storing data in dictionaries, lists, and tuples, cleansing data (regex), and saving the output in various data formats (pickle, json, txt). 


Outside of my internship, web crawling was used in my courses to collect data for data projects. Finding “the right data” for what I wanted to research was sometimes --most of the times-- the hardest task, but with web crawling, data collecting became both economic and fast. 


Considering its frequent usage and high functionality, I decied to document web crawling as it is (in my opinion) the most efficient way to collect data on the internet.


#### **Project Overview:**

For this project, I decided to crawl three websites: 

1.  user comments from [Daum News Article](https://media.daum.net){:target="_blank"}
2.  user comments from [Naver News Article](https://news.naver.com){:target="_blank"}
3.  user reviews from [Naver Movie Review](https://movie.naver.com){:target="_blank"}


Naver and Daum are both prominent web portals and search engines in Korea. Due to their characteristics, it is abundant with data. I also realized a lot of people searched tutorials on how to crawl data from these websites and thought it would be nice to share my experience crawling data from these websites.


#### **Web Scraping vs. Web Crawling**


A lot of the time, web crawling and web scraping are used interchangeably. But they have key differences. 


According to [Oxlyabs’ blog](https://oxylabs.io/blog/crawling-vs-scraping){:target="_blank"}, the differences are:



>Crawling, in most cases, goes hand in hand with scraping. When web crawling, you **download** readily available information online. And afterward, you filter out unnecessary information and **pick** only the one you require by scraping it. 



Another terminology that is used interchangeably is scraping and parsing. Parsing can be understood as being part of scraping or another step after scraping as parsing is extracting data from what has been scraped. 


Here’s a diagram: 


![WebScrape Overview](/assets/img/web-scrape.png)


I thought a good metaphor for the whole process was fishing. Let's say you are going fishing for barracuda. Data crawling is like going out fishing into the sea and sailing around the sea until you find the spot barracuda is most seen. After finding the spot, you would now fish until you catch a barracuda. Data scraping is like catching a barracuda. After catching a barracuda, you would go back to the shore and fillet the barracuda you caught into parts you need and throw out the rest. Data parsing is like filleting. You extract only the data you need.


Knowing these differences helped me grasp the whole data scraping process better. It also helps when reading the tutorials for each modules as you understand each aspects of the module better.


**Library/Framework:**


The most popular python web crawler libraries/frameworks are: 

1.  [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/){:target="_blank"} 
2.  [Selenium](https://selenium.dev/){:target="_blank"} 
3.  [Scrapy](https://scrapy.org/){:target="_blank"}


Each library has its advantages and disadvantages. Knowing the pros and cons helps choose the right one for your objective.


**Beautiful Soup**


According to this [complete guide](https://towardsdatascience.com/scrapy-vs-selenium-vs-beautiful-soup-for-web-scraping-24008b6c87b8){:target="_blank"} by towards data science, Beautiful soup is a **web scraper,** not a crawler. As it is a scraper, it depends on other libraries (requests, urlib2) to send requests to the target (html, xml) webpage. However, it is very easy to use and beginner friendly (helpful when understanding web scraping). 


I did not use Beautifulsoup in my project as Beautiful Soup did not provide the right parser for my objective.


**Selenium**


Selenium is a framework used to automate the process of web application such as logins. It can be used as a web crawler as well, especially for websites that are Core Javascript heavy. 


**Scrapy**


Scrapy is a web crawler framework that can crawl, scrape and parse. It also provides features that allows the user to specify proxy and cookies when sending requests to crawl web pages. Scrapy has a steeper learning curve but is one of the fastest and flexible frameworks.


![Modules](/assets/img/module_comparison.png)


Although the table above makes these modules appear mutually exclusive, they can be used in combination. For example, you can crawl using Scrapy and scrape the data with Beautiful Soup. For my project, I used scrapy as the crawler and python’s json module for scraping.

**Project Code**

You can find detailed information and code of each project in the README.md of each github page:

1.  [Daum News Article](https://github.com/hkimkim/data-crawling/tree/master/daum/){:target="_blank"}
2.  [Naver News Article](https://github.com/hkimkim/data-crawling/tree/master/naver/naver_news_scraper){:target="_blank"}
3.  [Naver Movie Review](https://github.com/hkimkim/data-crawling/tree/master/naver/naver_movie_review_scraper){:target="_blank"}

Check out my [github repo](https://github.com/hkimkim/data-crawling){:target="_blank"} with all the codes.

**Reference** :

*   [https://oxylabs.io/blog/crawling-vs-scraping](https://oxylabs.io/blog/crawling-vs-scraping){:target="_blank"}
*   [https://towardsdatascience.com/scrapy-vs-selenium-vs-beautiful-soup-for-web-scraping-24008b6c87b8](https://towardsdatascience.com/scrapy-vs-selenium-vs-beautiful-soup-for-web-scraping-24008b6c87b8){:target="_blank"}


