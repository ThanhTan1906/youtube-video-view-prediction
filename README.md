# YouTube Video View Prediction

## Project Overview

This project analyzes trending YouTube video data to identify the factors associated with video performance and develop a Machine Learning model for predicting video view counts.

The analysis covers data cleaning, feature engineering, exploratory data analysis, correlation analysis, and Linear Regression modeling. The project also provides data-driven recommendations for content creators who want to improve audience reach and video performance.

## Project Objectives

The main objectives of this project are to:

* Understand the distribution of YouTube video views
* Identify the factors associated with higher view counts
* Analyze video performance across content categories
* Examine the relationship between publication timing and video performance
* Create additional engagement, time-based, and content-based features
* Develop a Linear Regression model to predict video views
* Generate practical recommendations for YouTube content strategies

## Dataset

The project uses a dataset containing information about trending YouTube videos.

The main variables include:

* Video ID
* Video title
* Channel title
* Category ID
* Publication date
* Trending date
* Views
* Likes
* Dislikes
* Comment count
* Tags
* Publication time
* Publication day of the week

The dataset file used in the notebook is named:

```text
youtube.csv
```

> The dataset is not currently included in this repository. To reproduce the analysis, download the dataset and update the file path in the notebook.

## Project Workflow

The project follows the workflow below:

1. Import required libraries
2. Load and inspect the dataset
3. Check missing values and duplicate records
4. Clean and transform the data
5. Create new analytical features
6. Perform exploratory data analysis
7. Analyze correlations between numerical variables
8. Select model features
9. Split the data into training and testing sets
10. Train a Linear Regression model
11. Evaluate model performance
12. Interpret the results and provide recommendations

## Data Cleaning

The following data-cleaning steps were performed:

* Checked for missing values
* Identified and removed duplicate records
* Converted date-related columns into datetime format
* Prepared the dataset for analysis and modeling

The dataset contained no missing values, but duplicate records were found and removed.

## Feature Engineering

Several additional features were created to improve the analysis.

### Time-Based Features

* Publication day
* Publication month
* Publication hour
* Number of days from publication to trending

### Engagement Features

* Like ratio
* Comment ratio

The ratios were calculated as:

```python
like_ratio = likes / views
comment_ratio = comment_count / views
```

### Content-Based Features

* Video title length
* Additional title- and tag-related information

## Exploratory Data Analysis

### Distribution of Video Views

The distribution of video views is strongly right-skewed.

Most trending videos receive relatively moderate view counts, while a small number of highly successful videos generate extremely large numbers of views. This reflects the viral nature of content performance on social media platforms.

A logarithmic transformation was applied to improve visualization and reduce the effect of extreme values.

```python
np.log1p(views)
```

After the transformation, the distribution became more balanced and easier to interpret.

### Video Performance by Category

The analysis showed noticeable differences in view performance across content categories.

Categories such as category IDs 10, 24, and 28 had relatively high median view counts and included many high-performing outliers. These categories therefore appeared to have stronger viral potential.

Other categories, such as category ID 44, had lower and more stable view distributions.

This suggests that content category is an important factor associated with video performance.

### Video Publication Day

The number of uploaded videos increased during the working week and reached its highest level on Friday.

Average views also tended to increase toward the end of the week, with Friday showing particularly strong performance.

Weekend upload activity was lower. Saturday showed both fewer uploads and lower average views, while Sunday appeared to have lower competition and relatively stable performance.

These findings suggest that publication timing can influence video performance, but publishing more videos does not automatically generate more views.

## Correlation Analysis

The correlation analysis produced the following findings:

* Views had a strong positive correlation with likes, approximately `0.79`
* Views had a moderate positive correlation with comment count, approximately `0.50`
* Likes, dislikes, and comments were strongly related to one another
* Like ratio and comment ratio had relatively weak linear relationships with views
* Days to trending did not show a clear linear relationship with the other variables

The results indicate that audience engagement is strongly associated with video popularity.

However, correlation does not necessarily imply causation. For example, videos may receive more likes because they already have more views.

## Machine Learning Model

A Linear Regression model was developed to predict video view counts.

### Input Features

The model used the following features:

```python
features = [
    "likes",
    "dislikes",
    "comment_count",
    "like_ratio",
    "comment_ratio",
    "days_to_trending",
    "title_length"
]
```

### Target Variable

```python
views
```

### Train-Test Split

The dataset was divided into:

* 80% training data
* 20% testing data

A fixed random state of `42` was used to ensure reproducibility.

## Model Performance

The Linear Regression model achieved the following results:

| Metric             |                Result |
| ------------------ | --------------------: |
| R² Score           |               0.71498 |
| Mean Squared Error | 29,369,321,775,779.11 |

The R² score indicates that the selected features explain approximately 71.5% of the variation in video views.

The Mean Squared Error is large because the target variable contains extremely large values and follows a highly skewed distribution.

The Actual vs. Predicted plot showed that the model captured the overall pattern of the data. However, prediction errors increased for videos with extremely high view counts.

## Key Findings

The analysis produced several important findings:

* YouTube video views follow a highly right-skewed distribution
* A small number of videos account for extremely high view counts
* Likes have a strong positive relationship with views
* Comment count also has a meaningful relationship with video performance
* Content category is associated with differences in view performance
* Thursday and Friday appear to be effective publication periods
* Publishing more videos does not necessarily result in better performance
* Linear Regression explains approximately 71.5% of the variation in views
* Extremely viral videos remain more difficult for the model to predict accurately

## Recommendations

Based on the analysis, the following strategies are recommended.

### Improve Audience Engagement

Content creators should encourage likes and comments through:

* Clear calls to action
* Questions in videos and descriptions
* Active responses to viewer comments
* Community interaction

### Select Suitable Content Categories

Categories such as music and entertainment showed stronger view performance and greater viral potential.

Creators should consider audience demand and category-level performance when planning content.

### Optimize Publication Timing

Thursday and Friday appeared to be strong publication periods in the dataset.

However, creators should also test different schedules because audience behavior may vary by channel, location, and content type.

### Focus on Quality Rather Than Quantity

Publishing more videos does not automatically improve performance.

Creators should prioritize:

* Content relevance
* Production quality
* Viewer retention
* Audience value
* Consistent channel positioning

### Optimize Titles and Thumbnails

Titles and thumbnails influence whether users decide to click on a video.

They should be:

* Clear
* Relevant
* Visually attractive
* Accurate
* Consistent with the video content

## Limitations

This project has several limitations:

* The dataset focuses on trending videos and may not represent all YouTube videos
* The model uses engagement variables such as likes and comments, which are also influenced by views
* The relationship between engagement and views may involve reverse causality
* Linear Regression may not fully capture nonlinear relationships
* Extreme viral videos are difficult to predict accurately
* Category IDs were analyzed numerically rather than using full category names
* External factors such as subscriber count, thumbnail quality, watch time, and recommendation traffic were not included

## Future Improvements

Possible future improvements include:

* Applying a logarithmic transformation to the target variable
* Comparing Linear Regression with Random Forest and XGBoost
* Using cross-validation
* Evaluating the model with RMSE and MAE
* Applying feature scaling where appropriate
* Encoding category information
* Adding publication-hour features
* Including channel-level features
* Investigating multicollinearity
* Separating pre-publication and post-publication features
* Developing a model that predicts views using only information available before a video is published

## Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* GitHub

## Repository Structure

```text
youtube-video-view-prediction/
│
├── notebooks/
│   ├── README.md
│   └── Data_Analysis_and_YouTube_Video_View_Prediction_Model_Development.ipynb
│
├── .gitignore
├── LICENSE
└── README.md
```

## How to Run the Project

1. Clone or download this repository.
2. Open the notebook in Google Colab or Jupyter Notebook.
3. Download the required `youtube.csv` dataset.
4. Upload the dataset to your environment.
5. Update the dataset path in the notebook:

```python
df = pd.read_csv("your_path/youtube.csv")
```

6. Run all notebook cells from top to bottom.

## Notebook

The complete analysis is available in:

```text
notebooks/Data_Analysis_and_YouTube_Video_View_Prediction_Model_Development.ipynb
```

## Author

**Thanh Tan Vo**

Data Analyst Student

## License

This project is licensed under the MIT License.

