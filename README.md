# Web-Scraper Introduction 

<h2>Description</h2>
I wanted to focus more on how a webscraper works and the issues I found while creating this rather than just uploading something I needed at the time which other people may or may not need. Web scraping can do so many different things, my focus being automating a otherwise quite time consuming process for the sole gain of compettitve insights. Things to consider is the more data you scrape the better the processing power and bandwith youll typically need not to mention the biggest concern is websites may change their structure and destory the scrapping logic.

<br>In this case we will use rightmove and I will include screenshots down below to further demonstrate how to understand where to start in web scraping. In this scenario we will focus mainly on taking information from apartments things like price date ext.

<br> The best thing to do is to break down the problem step by step the first thing to do is define a url and then use requests to access the page using headless browser mode an example of this would be "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36".

<br> Once you have sucessfully made something that allows you to extract HTML you can start scraping down below will be two photos the first will be the one we are scraping from and the second will be the logic for this scrape once a basic concept is formed on how to scrape we can dive further into condtitional scraping. 

<br> In the code snippet down below we focus on the price for this particular rightmove website. We start by creating a function along with its name and passing soup which is our parsed HTML. Then the second line searches the soup object for the first div element with the class which matches the one specified. To do this youd go onto the website and rightclick on the element you want to inspect there will be a pop up of options and once you press the button "inspect" a developer tool will open with the a highlight of HTML which will be the element. Moving onto line 3 if there has been a sucsessful find of the element move on otherwise it will return price not found ( a simple debugging tool just to ensure that your code is identifying the correct element). The next step is similar to the first in which it just looks at the span within that class and if it is found it will move on otherwise it will break out and return price not found. Finally once it finds the data all that needs to be done is stripped which removes all trailing whitespaces from the text and the resulting text is assinged to the variable 'price'.

<br> This is just the bare basics of what can be done in web scraping, if we take it one step further we can look into conditional scraping where you may only want to scrape data in certain condtions, a good example of this within rightmove alot of agents put in the description the communal floor for certain developments, this is data that redundant towards me and often times is ignored so I had to ensure that this code accompanies for this. In the last photo shows a similar code but alot more indepth, the second half of this code snippet is about the paragrpah that is found at the bottom of the rightmove page. The fourth line contains something called a regex pattern what it does is take the whole HTML text and pick up all 1 or two digit numbers with st,nd, rd or th followed by floor and ignore all upercase and lowercase letters, the next line stores all of this. Once all these matches have been found the code loops through the text for each value and checks 50 words before and after to find the context of the match the if statements are used to either ignore of keep and sets the context if the words resident or swimming pool are withing the 50 word threshold then it ignores the match and goes to the next the stored value is then the returned value which will be put into excel.

<h2>Languages Used</h2>

- <b>Python</b> 

<h2>Libraries  Used </h2>

- <b>Tkinter</br>
- <b>Pandas</br>
- <b> Request</br>
- <b> BS4 </br>
- <b> RE </br>
- <b> Openpyxl </br>
- <b> Time </br>
- <b> Random </br>
- <b> Datetime </br>

<h2>Program walk-through:</h2>

<p align="center">
Rightmove Website: <br/>
<img src="https://i.imgur.com/yKF89xT.png" height="80%" width="80%" alt="Introduction"/>
<br />
<br />
Code snippter for price Scrape:  <br/>
<img src="https://i.imgur.com/jkR1CEY.png" height="80%" width="80%" alt="Introduction"/>
<br />
<br />
Floor Scraper: <br/>
<img src="https://i.imgur.com/Q8CgcPO.png" height="80%" width="80%" alt="Introduction"/>
