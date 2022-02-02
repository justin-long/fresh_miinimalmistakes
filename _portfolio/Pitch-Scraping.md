---
Title: "PITCHf/x Scraping"
excerpt: "Updating a Python-based web-scraper to construct a Pitchf/x database."
---

## Background Information

The main goal of this project was to construct a database containing [Pitchf/x](https://en.wikipedia.org/wiki/PITCHf/x) data. The MLB made the data available by posting it online in an XML format for every game under the gd2.mlb.com domain. I worked on this project during the Fall of 2018, while the MLB was still using that domain. At some point after that, the MLB migrated to [a new api](http://statsapi.mlb.com/api/) and made the data on gd2 inaccessible. 

## Methodology

The MLB releases data from each game and makes it publicly available, albeit, not in an easily accessible, downloadable format. Data from each game contains information about each team, player, each play of the game, and more importantly, each pitch thrown in the game. To access and store the data, a web scraper in Python was used. An outdated scraper was publicly available, although the structure of the website the MLB uses to store the data had changed enough to render the scraper unusable. The process to retrieve and open the URLs for each game had to be updated. The existing code also was not flexible enough to handle errors. If a game was delayed, missing innings, or there was a mismatched data in the URL, the scraper would essentially break, halting the entire process. Therefore, multiple sections of code needed to be added in order to make the scraper flexible enough to be able to run continuously and retrieve and store data from each game starting in 2008. The general process of the scraper is as follows:

 1. Enter the starting and ending date
 2. Using the starting data, the program will iterate day-by-day until it finds a day where at least one game occurred
 3. Each day has a separate page where all the basic game attributes are stored along with information about where the detailed information is stored
 4. The scraper will find the detailed id, and load the detailed game page
 5. It will then retrieve further detail about the game and teams from a subdirectory
 6. Information about each pitch is stored within a subdirectory divided by innings
 7. By iterating over each inning, the scraper will retrieve and store information about each pitch
 8. The process will continue for each game. When the last game is reached, it will then iterate day-by-day until if finds the next day where games occurred.

The data is then stored in two SQL databases, one containing pitch-by-pitch information, and the other containing information about each at-bat. Currently, the scraper requires anywhere between six and twelve hours per year. Therefore for 10 years of data, it could take between 60 and 120 hours to obtain all the data necessary.

## Results
I was able to construct a database containing pitch-by-pitch data from 2009 to 2019. There were existing packages and libraries available for r and python that made the data available as well. However, I wanted to create a locally stored database for my own use, and didn't want to be subjected to any limits imposed by the packages. 

This was one of my first experiences with going though someone else's code and updating it to run again, while making it more robust. I updated the python script and implemented exception handling as the goal was to have this run continuously until all games were scraped. I also updated the SQL files to create the tables and to load the data into a database. 

My starting point for the code and introduction to the Pitchf/x data was through [this post.](https://www.beyondtheboxscore.com/2015/9/24/9374949/a-new-python-based-pitchf-x-parser-scraper)