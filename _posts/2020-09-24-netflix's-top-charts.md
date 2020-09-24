---
layout: post
title: Netflix's Top Movie Charts
subtitle: Some interesting finds from looking at Netflix's top rated movies
author: Jacob Maxfield
tags: [charts]
comments: True
---

If you haven't heard of Netflix... Just kidding. You have.

Netflix has a [chart](https://www.imdb.com/chart/top) that shows the current 250 top rated movies. They also have a few others such as the "Lowest Rated Movies", which seems like a [disaster](https://www.imdb.com/chart/bottom):wink:, but I thought I'd see how ratings were like behind the scenes and not necessarily the polished numbers.

#### Before Thoughts

Initially, I didn't have any idea what I was going to research. That's not something I generally do or enjoy. (Then again, I don't think most people do.) I eventually thought about movies. I've almost always wanted to be a movie star, to **not** be in the crowd, but to be able to speak in an indirect way. Something I'm sure I'll get the opportunity to do in my life.

### Where to Look. Gathering the Data

I looked around for datasets on different sites, but couldn't find anything. After pondering for a what was probably a few hours, I thought about using an [API (Application Programming Interface)](https://en.wikipedia.org/wiki/API). In simplest terms, an API is a way of letting users/computers have access to data that isn't generally seen by people. Anyways, I knew that IMDb had an API, so I looked it up to see how I could use it. Unfortunately, it has a cost beyond 100 'requests' per day. I'm not exactly what is considered 1 request, but I decided not to risk it.

After about an hour or so, I decided to make the courageous move and _scrape_ the data. What does that mean? [Web Scraping](https://en.wikipedia.org/wiki/Web_scraping) is essentially just using a program to look at what's just under the hood (HTML) and extracting data from that layer. You can actually look at what the browser is doing right now. You can **right click** anywhere on the web page and select **Inspect**. You'll see a window appear that probably has a bunch of weird symbols called **tags**. That is what the program will scrape.

### The Scraping

I used three base sites: 
1. https://www.imdb.com/chart/top
2. https://www.imdb.com/title/tt + whatever the movies ID is
3. https://www.imdb.com/title/tt + ID + "/ratings"

I then needed to decide on how I was going to get this data: 
* ID, Title, Rating, Genres, Running Time, Release Date, Star Ratings, and Number of ratings.

I decided to use [BeautifulSoup](https://programminghistorian.org/en/lessons/intro-to-beautiful-soup), a web scraping tool used within the Python programming language, 
>(FYI, I **love** Python. It's absolutely fantastic for people interested in learning programming. It is very beginner friendly, and can be found [_here_](https://www.python.org/)!)

I am a noob when it comes to web scraping. I've only done it once or twice before this, so I spent the better part of a day figuring out where/how to get the data I wanted. I looked through a ton of html figuring out exactly where this data was stored.

I used [Google Colab](https://colab.research.google.com/) for most of web scraping, but I was having problems with it for some of it. It was showing the movie titles as Chinese characters, so I had to use my local computer to do that part. Besides that, I was able to get all the information I wanted. I completed one of the harder steps in this whole process.

By the way, I've stored the data in a CSV file you can find at my [GitHub](https://github.com/MaxTechniche/DS20_Unit_1_Build/blob/master/top_250_IMDb_movies_and_rankings.csv).

### Exploring the Charts
###### (All of the charts below are shown as averages unless otherwise specified.)

After loading in the data, one if the first things i did was check the value counts of the Release Years. I don't know why. Anyways, lo and behold, 5 pairs of movies with the same release date in the top 250! Here's the chart:
![](https://raw.githubusercontent.com/MaxTechniche/DS20_Unit_1_Build/master/tandem_release_dates_2.png)

Quick note someone noticed about the chart; Each of the pairs are relatively close to each other in terms of ranking. Don't know if it has to do with them being in the top movies or not, but still interesting.

The next chart is the total number of votes per star rating.
![](https://raw.githubusercontent.com/MaxTechniche/DS20_Unit_1_Build/master/stars_to_num_ratings.png)

I find this very interesting. The higher the rank, the more votes it has generally. Correlation of .592

My theory is that someone is more likely to vote, the more they like the movie, so other people know it's good. Another is, I think people are more likely to see the IMDb page of the movie the more it is rated.

Seems like that's true when it comes to a specific movie, but it definitely doesn't look like that when it comes to genres.
![](https://raw.githubusercontent.com/MaxTechniche/DS20_Unit_1_Build/master/genre_votes_and_star_rating_2.png)

Keep in mine that there are a couple of these genres that only have 1 or two movies in it, so the sample size is not enough to really guarantee that this is what it would be given a larger sample size. But also, this is just a mix of those that are in the top 250, so there's the argument there. Also, most of these movies have multiple genres and one of the genres are generally more present in that movie than others. That can easily skew the data.

Here's a graph of the average star rating of the movies that had come out by that year: 
![](https://raw.githubusercontent.com/MaxTechniche/DS20_Unit_1_Build/master/average_stars.png)

You can see how close the green line hangs to the blue one. That's telling us that there is a vast difference in the amount of voting between Males and Females.

One last graph shows the different averages and standard deviations of each of the age and gender groups.
![](https://raw.githubusercontent.com/MaxTechniche/DS20_Unit_1_Build/master/group_rankings.png)

So these are my questions for you:
1. Why aren't there more votes for women?
2. Why do older and younger people range more on ranking?
3. Why do females (except those that are 45+ it looks like) not like these movies as much?
