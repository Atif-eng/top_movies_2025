# 🎬 Top Movies 2025: The Cinema of Tomorrow

![Dataset Status](https://img.shields.io/badge/Dataset-Verified-success?style=for-the-badge&logo=kaggle)
![Domain](https://img.shields.io/badge/Domain-Entertainment_%7C_Movies-red?style=for-the-badge&logo=imdb)
![Size](https://img.shields.io/badge/Size-Top_25_Titles-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-CC0_Public_Domain-green?style=for-the-badge)

## 🍿 Overview
Welcome to the **Top Movies 2025** dataset!

This dataset provides a curated collection of the most anticipated and talked-about films released in **2025**. It captures the pulse of the box office and streaming platforms, featuring **IMDB Ratings, Vote Counts, and Plot Summaries**.

Whether you are building a **Movie Recommendation Engine**, analyzing **Audience Sentiment** for future blockbusters, or just want to know if *Snow White* flopped, this dataset is your golden ticket.

> **Note:** This dataset includes high-profile releases like the live-action *How to Train Your Dragon*, the new *Superman*, and the Formula 1 drama *F1: The Movie*.

---

## 📂 Dataset Structure

The dataset consists of a single CSV file: `Top_Movies_2025.csv`.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| **`Title`** | `String` | The official title of the movie. |
| **`Release Year`** | `Integer` | The year of release (All 2025). |
| **`IMDB Rating`** | `Float` | The current IMDB score (0-10). |
| **`Votes`** | `String` | Number of user votes (e.g., '393K', '1M'). |
| **`Plot`** | `String` | A short synopsis of the movie's storyline. |
| **`Poster URL`** | `String` | Direct link to the movie poster image. |

---

## 📊 Quick Insights (EDA)
Here is a snapshot of the cinematic landscape of 2025:

### 🏆 Top Rated Movies (Critics' Choice)
| Movie | Rating |
| :--- | :--- |
| **How to Train Your Dragon** | ⭐ 7.8 |
| **One Battle After Another** | ⭐ 7.8 |
| **F1: The Movie** | ⭐ 7.7 |

### 🗣️ Most Discussed (Highest Votes)
| Movie | Votes |
| :--- | :--- |
| **Snow White** | 393K |
| **Superman** | 377K |
| **Sinners** | 348K |

> **📉 The Controversy:** *Snow White* (2025) appears to be the most "talked about" film with nearly 400K votes, but holds a polarizing rating of **2.2**, suggesting massive audience debate.

---

## 💡 Potential Use Cases

This dataset is ideal for:

1.  **Sentiment vs. Popularity Analysis**
    * Compare `IMDB Rating` against `Votes`. Does high engagement always mean a good movie? (Spoiler: Look at *Snow White*).

2.  **NLP & Plot Analysis**
    * Use the `Plot` column to generate word clouds or classify genres based on keywords like "Viking", "Superhero", or "Racing".

3.  **Image Processing**
    * Use `Poster URL` to fetch images for building a movie poster classifier or a visual recommendation UI.

---

## 💻 Getting Started

### Python Example
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('Top_Movies_2025.csv')

# Clean the 'Votes' column (convert '393K' to 393000)
def clean_votes(vote_str):
    if 'K' in vote_str:
        return float(vote_str.replace('K', '')) * 1000
    if 'M' in vote_str:
        return float(vote_str.replace('M', '')) * 1000000
    return float(vote_str)

df['Votes_Numeric'] = df['Votes'].apply(clean_votes)

# Plot Rating vs Popularity
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='Votes_Numeric', y='IMDB Rating', hue='Title', s=100, legend=False)
plt.title('Movie Success 2025: Ratings vs. Popularity')
plt.xlabel('Number of Votes')
plt.ylabel('IMDB Rating')
plt.grid(True)
plt.show()
