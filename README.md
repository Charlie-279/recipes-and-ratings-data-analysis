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

To find potential associations within the data to explore, I created several plots and aggregated the data across certain columns. Two of these plots are shown below, along with one . There are 

Here is a histogram showing the distribution of n_ingredients, with each bar representing the number of entries in the DataFrame containing that number of ingredients. We can see that most of the recipes in the dataset have around 5 to 10 ingredients, with the mode of the data being 8 ingredients.

<iframe src="assets/n-ingredients-histogram.html" width=800 height=600 frameBorder=0></iframe>

Here is a line plot showing the average rating of recipes per year. There is some variation in this plot, particularly in the sharp fall in ratings in the years 2016 and 2017; however, there does not appear to be a trend as the years go by.

<iframe src="assets/avg-rating-per-year.html" width=800 height=600 frameBorder=0></iframe>

Lastly, I grouped the data by the number of ingredients for each entry in the DataFrame, and aggregated it using the mean function to find the mean of the average rating for each number of ingredients.

|   n_ingredients |   recipe_avg_rating |
|----------------:|--------------------:|
|               1 |             4.82175 |
|               2 |             4.73734 |
|               3 |             4.71927 |
|               4 |             4.69541 |
|               5 |             4.70567 |
|               6 |             4.67634 |
|               7 |             4.66519 |
|               8 |             4.65668 |
|               9 |             4.66115 |
|              10 |             4.65947 |
|              11 |             4.67827 |
|              12 |             4.67418 |
|              13 |             4.68648 |
|              14 |             4.65688 |
|              15 |             4.6792  |
|              16 |             4.67425 |
|              17 |             4.66918 |
|              18 |             4.72167 |
|              19 |             4.68489 |
|              20 |             4.68485 |
|              21 |             4.69057 |
|              22 |             4.83328 |
|              23 |             4.80406 |
|              24 |             4.73785 |
|              25 |             4.65741 |
|              26 |             4.82769 |
|              27 |             4.65238 |
|              28 |             4.83844 |
|              29 |             4.93088 |
|              30 |             4.78125 |
|              31 |             5       |
|              32 |             5       |
|              33 |             5       |
|              37 |             5       |

## Assessment of Missingness

## Hypothesis Testing

___