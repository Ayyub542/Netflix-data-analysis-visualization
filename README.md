# Netflix Data Analysis & Visualization

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** and **data visualization** on the Netflix Movies and TV Shows dataset.

The main objective of this project is to understand the distribution of Netflix content based on:

* Movies vs TV Shows
* Content ratings
* Movie duration
* Release year
* Countries producing Netflix content
* Movies and TV Shows released over the years

The analysis was performed using **Python**, mainly with **Pandas** for data manipulation and **Matplotlib** for data visualization.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data loading, cleaning, grouping and analysis
* **Matplotlib** – Data visualization
* **CSV Dataset** – Netflix Movies and TV Shows dataset

---

## 📂 Project Structure

```text
netflix-data-analysis-visualization/
│
├── netflix_titles.csv
├── netflix_analysis.py
│
├── movies_vs_tvshows.png
├── content_Rating_pie.png
├── movie_duration_histogram.png
├── release_year_scatter.png
├── top10_countries.png
├── movies_tv_shows_comparison.png
│
└── README.md
```

---

## 📊 Dataset

The project uses the **Netflix Movies and TV Shows dataset**, which contains information about Netflix titles such as:

* Show ID
* Title
* Type
* Director
* Cast
* Country
* Date Added
* Release Year
* Rating
* Duration
* Listed In
* Description

The dataset is stored in:

```text
netflix_titles.csv
```

---

## 🧹 Data Cleaning

Before performing the analysis, missing values were removed from important columns:

```python
df = df.dropna(
    subset=['type', 'release_year', 'rating', 'country', 'duration']
)
```

This ensures that the visualizations are based on records containing the required information.

---

# 📈 Data Analysis & Visualizations

## 1. Movies vs TV Shows

A bar chart was created to compare the number of Movies and TV Shows available in the dataset.

```python
type_counts = df['type'].value_counts()

plt.bar(
    type_counts.index,
    type_counts.values
)
```

### Visualization

![Movies vs TV Shows](movies_vs_tvshows.png)

---

## 2. Content Rating Distribution

A pie chart was used to visualize the percentage distribution of different content ratings.

```python
rating_counts = df['rating'].value_counts()

plt.pie(
    rating_counts,
    labels=rating_counts.index,
    autopct='%1.1f%%',
    startangle=90
)
```

### Visualization

![Content Rating Distribution](content_Rating_pie.png)

---

## 3. Movie Duration Distribution

A histogram was created to understand the distribution of movie durations.

The duration values were converted into integers before visualization.

```python
movie_df = df[df['type'] == 'Movie'].copy()

movie_df['duration_int'] = (
    movie_df['duration']
    .str.replace('min', '')
    .astype(int)
)

plt.hist(
    movie_df['duration_int'],
    bins=30
)
```

### Visualization

![Movie Duration Distribution](movie_duration_histogram.png)

---

## 4. Release Year vs Number of Shows

A scatter plot was created to analyze the number of Netflix titles released in different years.

```python
release_counts = (
    df['release_year']
    .value_counts()
    .sort_index()
)

plt.scatter(
    release_counts.index,
    release_counts.values
)
```

### Visualization

![Release Year vs Number of Shows](release_year_scatter.png)

---

## 5. Top 10 Countries

The top 10 countries based on the number of titles were identified and displayed using a horizontal bar chart.

```python
country_counts = (
    df['country']
    .value_counts()
    .head(10)
)

plt.barh(
    country_counts.index,
    country_counts.values
)
```

### Visualization

![Top 10 Countries](top10_countries.png)

---

## 6. Movies and TV Shows Released Over the Years

The dataset was grouped by release year and content type to compare Movies and TV Shows.

```python
content_by_year = (
    df.groupby(['release_year', 'type'])
      .size()
      .unstack()
      .fillna(0)
)
```

This helps visualize how the number of Movies and TV Shows changed across different release years.

### Visualization

![Movies and TV Shows Comparison](movies_tv_shows_comparison.png)

---

# 🔍 Key Analysis Areas

The project focuses on answering questions such as:

1. How many Movies and TV Shows are present in the dataset?
2. What are the most common content ratings?
3. What is the distribution of movie durations?
4. How has Netflix content changed across release years?
5. Which countries have the highest number of titles?
6. How do Movies and TV Shows compare in terms of yearly releases?

---

# 🎯 Learning Outcomes

Through this project, I practiced:

* Loading CSV data using Pandas
* Data cleaning and handling missing values
* Filtering DataFrames
* `value_counts()`
* `groupby()`
* `unstack()`
* Sorting data
* Creating calculated columns
* Exploratory Data Analysis
* Creating visualizations with Matplotlib
* Bar charts
* Horizontal bar charts
* Pie charts
* Histograms
* Scatter plots
* Line plots
* Saving plots as PNG images
  
# 📌 Future Improvements

This project can be extended by adding:

* More detailed country-level analysis
* Genre analysis
* Director and cast analysis
* Year-wise content trends
* Additional Matplotlib visualizations
* Interactive visualizations
* Power BI dashboard
* Advanced statistical analysis

## 📌 Conclusion

This project analyzed Netflix Movies and TV Shows using Python, Pandas, and Matplotlib**. It explored content types, ratings, movie durations, release trends, and top countries, providing practical experience in **data cleaning, EDA, and data visualization.



