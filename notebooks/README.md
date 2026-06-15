# Notebooks

This folder contains the main analysis notebook for the **YouTube Video View Prediction** project.

## Notebook

### `Data_Analysis_and_YouTube_Video_View_Prediction_Model_Development.ipynb`

This notebook performs exploratory data analysis and develops a Linear Regression model to predict YouTube video views.

The notebook was created and executed in Google Colab.

## Notebook Structure

The analysis includes the following sections:

1. Importing required libraries
2. Loading the YouTube dataset
3. Inspecting the dataset structure
4. Checking missing values and duplicate records
5. Cleaning and transforming the data
6. Creating additional analytical features
7. Performing exploratory data analysis
8. Analyzing correlations between variables
9. Preparing features for Machine Learning
10. Splitting data into training and testing sets
11. Training a Linear Regression model
12. Evaluating model performance
13. Interpreting results
14. Providing business recommendations

## Feature Engineering

The notebook creates several additional variables for analysis and modeling.

### Time-Based Features

* Publication day
* Publication month
* Publication hour
* Days from publication to trending

### Engagement Features

* Like ratio
* Comment ratio

### Content Features

* Video title length
* Additional title- and tag-related information

## Machine Learning Model

The notebook uses a Linear Regression model to predict video views.

The model uses engagement and content-related variables such as:

* Likes
* Dislikes
* Comment count
* Like ratio
* Comment ratio
* Days to trending
* Title length

The target variable is:

```text
views
```

## Model Evaluation

The model is evaluated using:

* R² Score
* Mean Squared Error
* Actual vs. Predicted visualization

The current Linear Regression model achieved an R² score of approximately:

```text
0.715
```

This means that the selected features explain approximately 71.5% of the variation in video views within the dataset.

## Requirements

The notebook uses the following Python libraries:

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
```

## Dataset

The notebook requires a YouTube dataset named:

```text
youtube.csv
```

The dataset should contain variables such as:

* `video_id`
* `title`
* `channel_title`
* `category_id`
* `publish_time`
* `trending_date`
* `views`
* `likes`
* `dislikes`
* `comment_count`
* `tags`

The dataset is not currently included in this folder.

## How to Run

1. Download the notebook.
2. Open it in Google Colab or Jupyter Notebook.
3. Upload the required `youtube.csv` dataset.
4. Update the dataset path in the data-loading cell.
5. Run all cells from top to bottom.

Example:

```python
import pandas as pd

df = pd.read_csv("youtube.csv")
```

## Important Notes

* The notebook should be run in sequence from the first cell to the last cell.
* The dataset path may need to be updated depending on the execution environment.
* The model uses likes and comments as predictor variables, so it is mainly suitable for explaining video performance after engagement data becomes available.
* A future version could develop a pre-publication model using only features available before a video is uploaded.

## Related Documentation

For the complete project overview, findings, limitations, and recommendations, refer to the main `README.md` file in the repository root.
