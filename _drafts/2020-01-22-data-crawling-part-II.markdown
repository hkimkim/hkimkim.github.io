---
layout: post
title:  "Project Data Crawling: Part II"
excerpt: "Scraping Daum News Articles"
date:   2020-01-22 08:13:02 +0530
categories: web development Flask
---

Daum is a prominent web portal and search engine in Korea. Daum also aggregates [news articles](https://media.daum.net/){:target="_blank"} from various publishers and provides a comment function for readers. This comment section was what I wanted to scrape.

## **Overview:**

*   **Objective**: scrape user comments from Daum news
*   **Requirements**: python 3.6+, jupyter notebook
*   **Modules used**: requests, json

*   **Scraped data features**:
    *   title: title of the article
    *   publishedDate: date the article was published
    *   id: Id of the each comment instance
    *   userId: Id number of the user
    *   postId: Id of the comment post
    *   content: comment by the user
    *   createdAt: date the comment was posted
    *   updatedAt: date the comment was updated
    *   childCount: number of replies to the comment
    *   likeCount: number of likes the comment received
    *   dislikeCount: number of dislikes the comment received
    *   recommendCount: number of likes - number of dislikes
    *   username: Daum user id
    *   displayName: display name of the user (a.k.a Daum nickname)
    *   commentCount: total number of comments the user has written on Daum



## **Steps**



(You can download the jupyter notebook for the tutorial [here](https://github.com/hkimkim/data-crawling/blob/master/daum/daum_news_scraper/daum_news_comment_scraper.ipynb){:target="_blank"}! )

### **1. Open web developer tool of the article link you are trying to scrape.**


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/console.png\")


Before scraping, I generally first go into the web developer tool of the web browser and click around the html to see how the webpage is structured. By looking at the structure, you can find the html tags of the data you want to scrape. If you are not familiar with html or web development, [selectorgadget](https://selectorgadget.com){:target="_blank"} is a great google chrome extension to find the html tags of the data you are trying to scrape. 

### **2\. Go into `Network > XHR` of web developer tool and click the file that starts with `comments?....` Then click `Preview` and you will see `postId`. Copy and paste the `postId` into the postId variable of the [jupyter notebook.](https://github.com/hkimkim/data-crawling/blob/master/daum/daum_news_scraper/daum_news_comment_scraper.ipynb)**


![\"\"](\"https://i.imgur.com/lWpyxWH.png\")


**jupyter notebook:**


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/postid.png\")


As the comment section of the daum article is filled in with data retrieved from web server using XHR object, scraping based on html does not work. So to scrape comments, request has to be sent to url of the API server that stores the comments, _not the url of the article_. The url of the API server requires a `postId` of the article, which we found in the above step.

The default API url format of Daum news article is:


> http://comment.daum.net/apis/v1/posts/{post\_id}/comments?parentId=0&offset={id\_of\_comment}&limit={number\_of\_comments\_to\_call\_from\_API}&sort=RECOMMEND


\*{ } are parameters for the url:


*   `post_id`: post id in API
*   `offset`: id of the comment (starting from 0)
*   `limit`: number of comments to call from api


### **3. Define functions to scrape and parse the data.**


I wrote two functions for scraping and parsing the data I need. The _**first function**_ is to scrape and parse the basic info of the article: title, published date, the total number of comments.


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/first.png\")


This function requires `postId` as a parameter (from the previous step) for the API url to send as request. In response to the request, a json is returned, which is parsed using the json module. In all, the function outputs a `list` of the scraped items ( \[title, date, total number of comment\] ). The total number of comments is an important argument for the second function.


The _**second function**_ is to scrape and parse the comment. It uses output from the first function as an argument.


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/second.png\")


The `postId` and the `total number of comments` are used as variables for the request API url. I looped through the `total number of comments`, and used each looped instance as argument for the API url. In other words, I sent a request that retrieves one comment instance from the API and scraped one comment at a time. The scraped data (which is a json file) is saved in `page` variable, which is then parsed using the json module. The output is a list of each comment in dictionary format.


### **4\. Run all the functions and convert the output to pandas dataframe.**


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/third.png\")

**The scraped output:**


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/daum_output.png\")



* * *

### **In sum:**


![\"\"](\"https://s3.ap-northeast-2.amazonaws.com/flask-uploads/uploads/daum_scraping.png\")


For my next post, I will share how I scraped [naver news article]() :) !


* * *


**My data crawling blog posts:**

*   [Part I: I will share the motivation and overview of my project. I will also cover the general concept of web crawling and the pros and cons of the popular web crawling python modules.]()
*   [Part II: I will share what I did to scrape comments of daum news article.]() 
*   [Part III: I will share what I did to scrape comments of naver news article.]() 
*   [Part IV: I will share what I did to scrape user reviews of naver movie review.]()
