# Spaceship Titanic Analysis - Kaggle
Collection of what I learned from the Kaggle competition Spaceship Titanic - thanks to Samuel Cortinhas
Link to competition: https://www.kaggle.com/competitions/spaceship-titanic

# 1. Exploratory Data Analysis and Feature Engineering
This part played the major role in this exercise. There were lots of ways to fill NaN values that were more or less guaranteed to be correct. Such examples:

  - People travelling in one group tend to be from the same planet. Given the Group feature, we can easily fill in the HomePlanet feature.
  - People with the same Surname are from the same planet - given two matching surnames and one planet, we can easily fill in the other one.
<p align="center" width="100%">
    <img width="50%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/homeplanet%20and%20surname.png">
</p>
  - The deck location and HomePlanet feature are strongly correlated. Given a deck we can tell from which planets the passangers may be, and given a planet the possible decks. This gives us a lot of strength to fill in NaN values.  
<p align="center" width="100%">
    <img width="50%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/homeplanet%20and%20deck.png">
</p>
  - People in groups are not only from the same planet, but also the same location - it is easy to see for example on the side paramter - which side of the ship they are located on. The exact deck and number aren't that strongly correlated though.
 
 <p align="center" width="100%">
    <img width="50%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/unique%20cabinsides%20per%20group.png">
</p>
 - The amount of expenses and CryoSleep are very important features. People in CryoSleep tend to not spend any money (they are asleep). 

<p align="center" width="100%">
    <img width="25%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/cryosleep%20and%20spending.png">
</p>
  - Surnames are usually also unique to groups - people travelling in groups are mostly families. We can with a pretty good precision fill in the remaining Surnames.
 <p align="center" width="100%">
    <img width="25%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/surnames%20to%20groups.png">
</p>

Although the Surname seems unimportant, it played a great role at filling other NaN values.

# 2. Models
Thanks to our feature engineering, we could train decent models. One could notice great differences before and after properly filling NaN values.
Our results were the following: 
<p align="center" width="100%">
    <img width="25%" src="https://github.com/CsabaDanielFarkas/spaceship-titanic-analysis-kaggle/blob/main/Images/results.png">
</p>
We used SVC, LGBM and CatBoost for our final predictions. Our final Kaggle score was 0.805.
