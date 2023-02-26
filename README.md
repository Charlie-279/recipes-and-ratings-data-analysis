# Recipes and Ratings Data Analysis
A data analysis project concerning recipes and ratings on food.com, for DSC 80 at UC San Diego.

By: Charlie Gillet (cgillet@ucsd.edu)

---

## Introduction

My analysis is centered around the question: Do recipes with 15 or more ingredients tend to have higher ratings? Answering this question is useful practically as it can suggest which recipes should be chosen when you are cooking. It can also provide a general idea of whether or not it is helpful to include more ingredients in a recipe.

This project makes use of two datasets from food.com, one containing recipes and the other containing reviews and ratings submitted for the recipes in the first dataset. These two datasets were then left merged into one larger dataset, which makes it easier to work with and to identify which ratings correspond to wihch recipes. This resulting dataset contains 234429 rows and 26 columns, and but only some of the columns are relevant to my analysis. These columns are:
- 'id': ID of each recipe
- 'recipe_avg_rating': average rating of each recipe
- 'n_ingredients': number of ingredients used in the recipe

## Cleaning and EDA

To clean the dataset, I first left merged the raw recipes and raw interactions DataFrames in order to have the correct ratings on each row. I then replaced all of the ratings of 0 with NaN, which is reasonable because a typical star rating system uses 1 as the lowest rating, so it is likely that the ratings of 0 are the dataset's way of marking missing ratings. Additionally, I inspected one of the recipes that was given a 0 rating on food.com. I found the review corresponding to the 0 star rating, and it does not show a star rating like the other reviews. Having ratings of 0 in the dataset would decrease the average ratings of each recipe, so it is best to exclude them from calculations.

Next, I added a column named 'recipe_avg_rating', which assigns the average rating of each recipe to its corresponding row. I then took each value in the 'nutrition' column, stored as a string, and converted it into 7 individual columns, one for each nutritional category, stored as floats. Since the dates in the 'submitted' and 'date' columns were in string form, I converted these columns to the datetime data type so that operations could be performed on them. Following this, I added numeric year and month columns so they would be easier to perform operations with.

The first few rows of the resulting DataFrame for the colmuns relevant to this investigation are shown here:

|     id |   n_ingredients |   recipe_avg_rating |
|-------:|----------------:|--------------------:|
| 333281 |               9 |                   4 |
| 453467 |              11 |                   5 |
| 306168 |               9 |                   5 |
| 306168 |               9 |                   5 |
| 306168 |               9 |                   5 |


For website:

## Assessment of Missingness

## Hypothesis Testing

___