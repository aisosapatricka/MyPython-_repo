# 📊 Student Marks — Data Cleaning & Visualisation

## 📌 Overview

This project was completed as part of my **Level 3 Digital Skills Bootcamp (Data Technician)**. Using a student marks dataset (class, gender, score), I used Python with **Pandas**, **Matplotlib**, and **Seaborn** to load, clean, group, and visualise the data — turning a raw CSV into a set of clear charts that summarise performance across classes and genders.

---

## 🧠 Skills Demonstrated

### Loading & exploring the data

```python
import pandas as pd

df = pd.read_csv('student.csv')
df.head()
df.info()
df.describe()
```

### Grouping & aggregation

```python
# Average score by class
df.groupby('class')['score'].mean()

# Number of students per class
df['class'].value_counts()

# Average score by gender
df.groupby('gender')['score'].mean()
```

### Pivot tables & conditional logic

```python
# Class vs gender pivot table of average scores
pivot = pd.pivot_table(df, index='class', columns='gender', values='score')
print(pivot)

# Custom grading function using if/elif/else
def grade(score):
    if score >= 85:
        return 'A'
    elif score >= 70:
        return 'B'
    elif score >= 60:
        return 'C'
    else:
        return 'D'

df['grade'] = df['score'].apply(grade)
```

### Exporting cleaned results

```python
df.to_csv('student_with_grades.csv', index=False)
```

---

## 📈 Visualisations

**Average Marks by Gender** — comparing mean scores across gender groups after cleaning.

**Number of Students in Each Class** — a bar chart showing class sizes across the dataset.

**Marks Distribution by Class (Boxplot)** — spread and median scores per class, useful for spotting classes with wide performance gaps.

**Distribution of Marks (Histogram)** — the overall shape of the marks data, showing where most students' scores cluster.

---

## 🧹 Data Cleaning Notes

Before these charts were produced, the class labels needed real cleaning — the raw data contained inconsistent entries such as **"FIVE" and "FIFTH"** referring to the same class, spelling issues like **"FIGHT"**, and a **"NAN" category** appearing as if it were a genuine class rather than a missing value. Working through this was a useful reminder that "cleaned data" is a process, not a single step — a chart can look finished while still carrying labelling issues that only show up once you look closely at the axis categories rather than just the shape of the bars. Fully resolving inconsistent categories and true missing values would be the next step before treating this as production-ready output.

The boxplot also surfaced a genuine **outlier** in class "SIX" (a score sitting well below the rest of that class's distribution) — a good example of why boxplots are useful beyond just comparing medians.

---

## 🛠️ Tools Used

- **Python** — Pandas, Matplotlib, Seaborn
- **Jupyter/Colab notebook** environment
- Core Python: variables, functions, `if`/`elif`/`else` logic, `for` iteration via Pandas' `.apply()`

---

## 📚 Key Takeaway

This project reinforced that grouping and aggregation (`groupby`, `value_counts`, pivot tables) are what turn a flat spreadsheet into something that actually answers a question — but it also taught me to treat "cleaned" as a claim to verify, not assume. Spotting the "NAN" and duplicate-label issues in my own charts was a genuinely useful lesson in checking output critically rather than moving straight from code to conclusion.

---

<img width="1778" height="1099" alt="Screenshot 2026-08-20 161657" src="https://github.com/user-attachments/assets/9f46c25f-e50a-40cd-878e-d0f929f94645" />
<img width="1797" height="1124" alt="Screenshot 2026-08-20 161714" src="https://github.com/user-attachments/assets/0ab0c614-b44a-4e27-9fba-f78268a24ee1" />
<img width="1776" height="990" alt="Screenshot 2026-08-20 161640" src="https://github.com/user-attachments/assets/65a25664-ac73-455c-872c-c6f8ae013d31" />
