---
layout: post
title:  "Web Development"
excerpt: "What I learned from web development"
date:   2019-11-14 07:38:29 +0530
categories: Web-development Flask HTML/CSS
---
#### Motivation

As a kid who spent a lot of time on youtube, I’ve always felt web development was a must-have skill as an internet generation kid (owe it to the founders of the internet to at least know how it worked). That sense of responsibility naturally developed into penchant for websites. From my pre-teen years obsession with piczo to my highschool years tweaking wordpress for a school charity event, I would spend hours and hours on tuning and customizing “websites”. Perfecting it gave me so much thrill.

The interest continued into my college years. But rather than depending on a service platform to generate my vision of a website, I wanted to be independent and self-sufficient.

#### Learning


As any skill learning happens these days, I started out reading online tutorial blogs and subscribing to online courses. But contrary to my zeal, I barely managed to finish tutorials and courses, and ended up taking long hiatuses, just to realize the next month that the subscription fee already had been billed.

What led me to long hiatuses was the complexity of web development. I had naively or somewhat presumptuously thought by learning _one_ programming language ( \*cough\* python), I could generate the elegant websites you now effortlessly see anywhere online.

But to deploy the website that I envisioned, CSS, HTML, Python, and SQL all had to work in unison. This meant when I managed to finish learning one component of web development, another component awaited to be mastered, which made the tutorials seem endless. The intertwinedness of each component also made the learning overwhelming.

Looking back, I should have really taken the time to understand the structure of the web development before tackling tutorials as it would have helped me understand the functionality of each component better.

**Simplified Overview of Web Development**

![WebDev Overview](/assets/img/webdev_framework.png)

Helpful Resources:


*   Detailed [Video](https://www.youtube.com/watch?v=0pThnRneDjw) that explains web development and its trend
*   Detailed [roadmap of Web development](https://dev.to/javinpaul/the-2019-web-development-frontend-backend-roadmap-4le2)


Even though I had finished tutorials (after taking many breaks), I felt uncertain of my abilities as I felt I was merely copying rather than writing my own codes. Mimicking was really helpful when learning the basics, but when it came to more advanced levels, the technique wasn’t effective for me. The uncertainty of my ability combined with my eagerness made me jump around learning the parts of web development --learning html and then partly tackling python flask, then back to css-- which hindered progress and added more frustration. As I understand now, due to the layerness of web development components, it is better to learn each component in certain order. For me, learning frontend and then learning backend made more intuitive sense as I could link backend to frontend and see how backend functioned or outputted on client side.


Order to tackle web development (from personal experience):

1.  HTML
2.  CSS (Bootstrap4)
3.  **Try making static website**
4.  Python Flask (Backend)
5.  SQL (Data server)




### Trial 1: html + css


After many tutorials and long hiatuses (and growing doubt for my abilities), I decided to just try building my first static website. Instead of waiting till I learned the backend, I thought I should just create what I can on the frontend, make it exist on the web, and improve on it as I go.


After watching a two hour youtube video on the basics of html and css as a refresher, I started wireframing the website. Browsing around other people's personal website, I realized the most important component of a website is the navigation bar. More specifically the position of the navigation bar (horizontal or vertical). I thought navigation bar not only showed the general overview but also set the tone for the website. For me, a horizontal navbar felt more formal whereas the vertical bar more casual.


I played around with the position of the navigation bar and its subsequent designs, revising the html and css and eventually decided upon a vertical navigation bar design. After grappling with it for a month, I arrived at a design I was pleased with and went on to buy my first domain name from name cheap, and deployed it on netlify



**Steps I took:**


1.  Outline the rough content I want on the website. 
2.  Draft wireframes based on outline (for desktop screen size). 
3.  Script the design with html and css (bootstrap4).
4.  Write the content.
5.  Draft wireframes for other screen sizes (media queries).
6.  Script the design for media queries with html and css.
7.  Deploy using [netlify](https://www.youtube.com/watch?v=bjVUqvcCnxM).



### Trial 2: static + flask


After leaving it as it is for months, I revisited the website. The website felt too basic, but also messy, cramped in with too much content. So I decided to redesign the website.


This time I wanted a horizontal navigation bar as it felt more organized. Contrary to my worries, writing html/css came at ease and I was able to write the code for the design I wanted in two days. Feeling somewhat confident of my skills, I decided to apply backend to my website (python flask). I had previously tried flask but lost interest due to the lack of front-end element to the learning (Whatever I was creating with just flask wasn't meeting my expectation to what a 2019 website should look like). Since I had a static website now, flask seemed applicable. I applied a [simple flask web framework](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world) by following this [youtube tutorial](https://www.youtube.com/watch?v=zRwy8gtgJ1A&t=10s).



**Steps I would take if I redid it:**

1.  Outline the content I want on the website. 
2.  Draft wireframes for each content and how each page is linked to each other based on outline. 
3.  List up html and flask route needed for each content.
4.  Script the design with html and css (bootstrap4).
5.  Write the code for route in routes.py in flask project directory.


### Trial 3: static + flask + MySql

But another problem arised. Since I had not considered the functionality/backend of the website, the ui/ux became awkward. So front-end had to be redesigned.


As I wanted a blog functionality added to my website, the structure of flask had to be altered as well. Instead of the simple flask web framework, I applied the [application factory](https://flask.palletsprojects.com/en/1.1.x/patterns/appfactories/) setup, as it modularized the parts of app, making maintenance easier.

Restructuring into application factory framework was more challenging than I expected. As my website had its own unique structure, following the tutorials had its limitations. I did restructure based upon the tutorials, but debugging was what really helped me understand the application factory framework more thoroughly.


By adding the blog functionality, I also had to add a data server to the website. I used SQL(MySQL), as it was something I had learned but hadn’t tried applying to an application. As I had set up MySQL on my terminal before, there was less error handling than I expected. As I had some experience with SQL, SQLAlchemy  had a shallow learning curve. The challenging part was the migration (data migration is updating the changes made on local data server you use for development to the production web server you use for web deployment). Again, merely following the tutorials didn’t work for my website. I realized the biggest part people neglected to write in flask-migrate tutorials is that local data server and the web data server had to be in sync or had to be a copy of one another. If changes are not being updated to the web server even after migrations are made, try using [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) (if you are using MySQL) or something equivalent to whatever SQL you are using to copy the local data server db to the web server db as this might solve the problem.

As my website was no longer static, it could not be deployed using netlify. As an alternative, I used heroku. Heroku was pretty easy to learn following the tutorials.


**Steps I would take if I redid it:**

1.  Outline the content I want on the website.
2.  Draft wireframes for each content and how each page is linked to each other based on outline. 
3.  List up html and flask route needed for each content.
4.  Outline the data frame structure needed for functions of website.
5.  Set up flask using application factory framework.
6.  Create a virtual environment and run on virtual environment.
7.  Write the code for route in routes.py in flask project directory. Run locally to see if the routes work.
8.  Script the design with html and css (bootstrap4).
9.  Set up your data base on your local data server.
10. Write the code for data structure in models.py in flask project directory.
11. Write up the settings of your local database on config.py. Run locally and check if it connects to database.
12. Set up Heroku (web server database, procfile, sync to github if you have one).
13. Apply data migration.
14. Deploy it on heroku.


**Tech Stack:**

Frontend:
1.  Html
2.  Css (bootstrap4)

Backend:

1.  Flask
2.  MySQL
3.  SQLAlchemy
4.  Flask-migrate
5.  CKeditor

### Takeaways


Web development was something I really wanted to do for a very long time. Struggled a lot at first trying to know "everything", but when I just let go a little of my obsession on trying to do everything "right" and "perfect", and worked with what I could do, I felt content. Although it questioned my patience many times, the feeling of content fueled me to continue on and I eventually arrived at a point I wished myself to be. Although considering the complexity of web development, there are still many things I haven't fully grasped (javascript) and hope to learn in the future, but this has been one of the most fulfilling experiences I've had and I'm really glad I tried.


### Update
- [Jan 2022] I'm finally taking Web development course for my masters program! 
- [Feb 2022] I built a [web game](https://astro-trash.netlify.app/) using typescript with my friends at Hackbeanpot Hackathon