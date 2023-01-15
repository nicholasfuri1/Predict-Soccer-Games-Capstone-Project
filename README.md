# Capstone-Project
## Models that predict the outcome of soccer games

Problem Statement:
The data that was acquired is of the following nature: stats of each game, betting
odds and sentiment analysis (subjectivity and polarity) of the fan base and media
from twitter.
The main goal of my project is to predict the winning team in each soccer game
played in the Italian league (Serie A) through the different types of data which
describe the soccer environment in the games (games stats), with the betting odds
provided by sites and then with an overall understanding of the opinions
(subjectivity) and of the emotions (polarity) on twitter.
Through the creation of models that can predict winners in soccer games, wealth
can be created.
Background on the subject matter area:
Soccer is starting to be an industry which is becoming more data oriented. In the
last decade there has been a lot more data collection both in official games and in
training environments for the teams. The idea is to use the data provided by the
web to predict soccer games.
Today to predict games, data such as injuries, suspensions and other factors that
can affect a team’s performance are being used by news outlets and betting
companies to predict winners and losers.
Details on dataset:
Part of the dataset (soccer stats and betting odds) are provided by an online site
(https://www.football-data.co.uk/italym.php ), which keeps track of all the soccer
matches in the past 20 years. The site provided the following data:
- Date , is the day and year of when the game occurs
- Team, is the name of the team
- TS, the number of Shots for the team
- TST, number of Shots on Target for the team
- TC, number of corners for the team
- TF, number of fouls committed
- TY, number of yellow cards for the Team
- HR, number of red cards for the Team
- Opponent, the name of the team which the Team played against
- OS, number of Shots of the Opponent team
- OST, number of Shots on Target for the Opponent Team
- OC, number of corners gained from the Opponent Team
- OF, number of fouls committed by the Opponent Team
- OY, number of yellow cards for the Opponent Team
- OR, number of red card for the Opponent Team
- HTTG, number of goals in the half time from the Team
- HTOG, number of goals in the half time from the Opponent
- new_HTR, is the results in half time which can be Win, Lose or Draw and
refers to the Team
- FTTG, number of goals in the full time from the Team
- FTOG, number of goals in the full time from the Opponent team
- new_FTR, is the results in full time which can be Win, Lose or Draw and refers
to the Team
- Avg_Odds_Away, average of the betting sites for the Away odds
- Avg_Odds_Draw, average of the betting sites for the draw odd
- Avg_Odds_Home, average of the betting sites for the home odds
- Venue, if the team is playing at home or Away

The sentiment analysis of each game was scraped from twitter. The package that
was used is snscrape.modules.twitter. With this module it’s possible to scrape a
set amount of tweets on twitter based on a hashtag with limit time frame. Once the
tweets were scraped through the text.blob module you can identify the polarity
and in the subjectivity of each game. This type of data is used to categorize the
emotions (polarity) and the opinions (subjectivity) of the media and fan base.
The time frame of the total data frame goes from 2015 to the end of 2022, with a
total of 5700 rows.

Summary of cleaning and preprocessing:

In the data frame the following EDA has been performed:
- Since the dependent variable that we want to predict is based on the final
result of a winning team, the distribution of this results are analyzed.

![image](https://user-images.githubusercontent.com/117306615/212572552-f5180da3-8854-4c3b-8ab1-07a4dfb262e3.png)


- The chart above suggests that in general, there is an equal
distribution of the winning and losing results (a team that wins always beats
an opponent team). The draws are less compared to the wins and losses.
In the bottom of the chart there is the percentage of the distribution.
Considering such results, the idea is to create a binary dependent variable,
with 0 that identifies the loses and draws of a team, and 1 the wins of the
team.
- Analysis of how the team performs when they play at home or away.

![image](https://user-images.githubusercontent.com/117306615/212572603-180bef9a-43b5-430a-83fc-ae54b4966d57.png)


- Its possible to deduced from the graph above that teams that play at home
win most of their games, while if they play away they tend to lose more
games.
- I Created variables that keep in mind this type of performance of the team
based on venues.


Feature engineering:
- Historical Performance: this variable keeps track of how each team performs
against each opposing team. There are always teams that historically
perform bad against other teams. The idea is to try to give that type of data
to the models. The variable will be a winning percentage ratio.
- Rolling Averages: the idea is to create rolling averages for each team
calculated with a lag of 3 games. the rolling averages are calculated on the
soccer stats. In addition, considering the EDA conducted teams tend to
have different performance based on the Venue (Home or Away). The
rolling averages are calculated dividing the main data frame into Home
venues and Away venues, at the end of such calculation the two data frame
will be merged again.
- Dummies: The dummies that are created came from the columns of the
‘Team’ and of the ‘Opponent’. These are categorical values and in order to
feed the models this type of variable it was necessary to create dummies
for the two columns.
- Codifying dates: to get patterns based on dates, the date column was
codified in several ways. Code for each day of the week, each month of the
year and each year. These variables are able to gather information based
on performance of teams during the time lapse of the data frame.


Insights, modeling and results:
The models that have been used in this project are the following:
- Logistic Regression
- KNN
- SVM
- Decision Trees
- Random Forest
- XGBoost
- Naive Bayes

These models have been selected because they are some of the best models that
are able to predict outcome with a binary dependent variable.
Results from the model comments:
- All the results focus on how the models are able to predict the outcome of
dependent variable 1.
- The goal of this project is to identify the best model, but at the same time
there isn’t a better model overall.

![image](https://user-images.githubusercontent.com/117306615/212572648-a12e8c68-6c76-45c5-87a2-91715e5d4481.png)


- Betting is also a strategy, and the best models depends on what the bettor is
aiming for.
- If the bettor wants to have a high-test Accuracy and able to detect both
Loses/Draws (outcome 0) and Wins (1), the best model to use is the Decision
Trees (72%)
- If the bettor is aiming to have a higher Precision in identifying the wins, then
the model to uses is the SVM model with a 69% score. This model has the
lowest score in Recalls (33%). Another alternative could be the Logistic
Regression model, which has the second-best Precision score (67%) but a
higher recall score (44%)
- If the bettor wants to have a model which out of the whole baskets of positive
can identify more Wins, then the best model is Naive Bayes with a 62% Recall
score. This model at the same time has a precision of (59%).
- If the bettor wants a model that has the highest average of Precision and
Recall score Naive Bayes has the best F1 score (69%).

Findings and conclusions:

It is possible to create models that can identify the winning team of each soccer
game. The several models built and explained in the paragraph above can be
used based on the betting strategy that the bettor wants to apply.
I believe that all the models created can increase their scores by:
- Improving the dataset with the addition of more soccer stats. These stats
could be found by other web sites and acquired through scraping or with an
API
- Change the sentiment analysis tool and increasing the number of tweets
scraped for each game.

