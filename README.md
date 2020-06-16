# Executive Summary

- This project was part of a hackathon. I had roughly eight hours to find a dataset and use it to build a predictive model
- The dataset I used was the Jeopardy dataset located in the [data](./data) folder
- I created a classifier capable of predicting whether or not a clue was a Daily Double with 98% accuracy

# Background

[Jeopardy James](https://en.wikipedia.org/wiki/James_Holzhauer) had one of the most dominant runs in Jeopardy history by utilizing an uber-aggressive strategy that involved "hunting" for Daily Doubles. James recognized the strategic importance of finding the Daily Doubles, and as such, specifically targeted clues he thought were likely to be Daily Doubles.

With a dataset representing 35 seasons worth of Jeopardy clues, I wondered if I could build a model to predict whether or not a clue was a Daily Double (based on clue value and other factors).

# Data Acquisition, Cleaning, EDA

I found this dataset online through a Reddit forum. There was not much cleaning necessary, except for having to remove older clues that used a different scoring system. It was during this phase, however, that I discovered a potentially fatal flaw with the dataset. Most of the clues are marked with their traditional values, but the Daily Doubles are marked with the amount of money the contestant decided to wager. As such, the Daily Doubles almost always have irregular clue values.

With this flaw, it was impossible to build a model capable of being used for regular Jeopardy play. I figured that if the model was not going to be useable, it should at least be highly accuracate. So I created a column for `is_irregular_value` which signaled if a clue had an irregular clue value (and was thus assuredly a Daily Double).

# Modeling

I fit both a logistic regression and random forest classifier. The random forest model performed best with an accuracy of about 98%. It seems that for both models, what helped most was the data leakage present in the `is_irregular_value` column. I was okay with this because I knew the dataset couldn't be used for the purposes I had in mind, so a good accuracy score was the most I could hope for.

# Conclusions

- Being a Jeopardy fan, I had high hopes for using this dataset
- As it turned out, an odd method of entering data made it impossible for me to use as I had hoped
- Regardless, the model performed reasonably well (although it is not generalizable)
- I would love to have a Jeopardy dataset that has Daily Doubles with their original value listed instead of the amount wagerered. This would make it possible to build a generalizable model