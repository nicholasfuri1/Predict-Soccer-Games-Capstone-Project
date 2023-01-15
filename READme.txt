BrainStation-Capstone-Project

Name student: Nicholas Furi
Project: Predict winner soccer games

In the following there is a description of the files/notebook created for the accomplishment of the project

Part_1_AquisitionData&Cleaning --> In this notebook is provided analysed and collected part of the dataset which came from website (https://www.football-data.co.uk/italym.php) and by tweet scraping on twitter

Part_2_EDA \'97> In this notebook EDA have been conducted.

Part_3_Models \'97> In this notebook two things are being done:
    				 - Feature Engineering such as:
      			         	 - Variable that keep track of how each team performed in the pass against each opponent. The variable is a winning percentage ratio
                                   	 - For each soccer stats are calculated rolling averages with a lag of 3 games\
                                   	 - Changing location of the Betting Odds
                                    	 - Codifying and binarizing columns
  				  - Fitting the dataset in the following models:
      					  - Logistic Regression
     				          - KNN
      					  - SVM
       					  - Decision Trees
     					  - Random Forest
    				          - XGBoost
      					  - Naive Bayes

CSV Campionati -->  In this folder there are the files downloaded by the website that provided with the soccer stats and the betting odds (https://www.football-data.co.uk/italym.php)
DataFrameTwitter --> In this folder is possible to find the files updated with the tweets data. This csv files have been used to build models.
Report Capstone -->  Is the pdf file that provides the reports of the capstone

