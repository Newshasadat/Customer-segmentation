# AI Tools Usage Among Software Developers

## Problem Statement

We will analyze survey responses to understand how software developers are using AI tools.  
The goal is to identify people’s pain points and find a market gap to exploit.

---

## Desired Outcome

This project aims to provide:

- Evidence of whether AI tool usage differs between developers with different levels of experience.
- An analysis of the factors that determine how people assess the usefulness and trustworthiness of AI tools.

---

## Data Source

The data comes from the **Stack Overflow Developer Survey**, made available by Stack Overflow:

https://insights.stackoverflow.com/survey

Most of the data is categorical because the source is a survey containing many multiple-choice questions, resulting in categorical values.

---

## Data Dictionary

The data dictionary is provided in two parts, both included in the supplementary materials:

- **`survey_results_schema.csv`**  
  Provides a question-by-question breakdown and documents which survey question each column represents. Some questions have their answers distributed across multiple columns.

- **Survey PDF**  
  A PDF copy of the original survey. It allows us to directly observe the data-generating process, which is rare.

---

## Project Progress

The analysis follows these main stages:

1. Read the survey to understand the exact questions that were asked.
2. Examine the data dictionary and dataset to understand how survey questions relate to the columns.
3. Explore the data by examining common properties such as missing data, outliers, and similar characteristics.
4. Identify the questions and columns relevant to the research questions.
5. Analyze the relationships between the selected variables and the AI-related outcomes of interest.
6. Summarize the findings.

---

## Analysis Steps

### 1. Investigate Missing Data

Remove rows where all answers were missing.

### 2. Investigate AI Favorability and Trust

 Analyze the questions related to attitudes toward AI, including favorability, and trust. 

 Compare respondents who currently use AI tools with those who do not.

2.1 AISelect 

The distribution of `AISelect` was analyzed to understand overall AI adoption. (bar chart)

2.2 AISelect × AISent

A Crosstab and pivot table and Heatmap were created for:

`AISelect × AISent`

to examine the relationship between AI usage and interest.

2.3 AISelect × AIBen

A Crosstab and pivot table and Heatmap were created for:

`AISelect × AIBen`

to examine the relationship between AI usage and trust.



### 3. Investigate AI Tool Usage Purposes

 Tabulate sentiment and trust in relation to different AI use cases.

The `AItoolCurrentlyUsing` column contains the different ways users currently use AI, such as coding and other activities.

For each use case:

* The percentage of interested users was calculated using `AISent`.
* The percentage of users who trust AI was calculated using `AIBen`.

This helps identify which AI use cases are associated with higher levels of **interest and trust**.


-Bar chart showing what percentage of AI users ticked each “Currently using” option
-crosstab and Heatmap of different AI tool use cases vs. view on favorability/trustworthiness

### 4. Investigate Job Roles of AI Users

Analyze AI usage across job roles and create combined **“Developers”** and **“Engineers”** categories.


-Heatmap showing AI use cases across different job roles


### 5. Investigate Coding Experience and AI Trust/Favorability

Examine the relationship between coding experience and AI trust/favorability by grouping years of experience into discrete categories.
 

 
- Distribution of AI users’ coding experience (bar chart)
- Distribution of years of experience across answers to the AI favorability/trust question (boxplot)
- Distribution of the newly binned years of experience data (bar chart)
- Heatmap of favorability/trust vs. experience (heatmap)
- calculate Spearman’s rank correlation



### 6. Investigate Market Opportunities for AI Products

Investigate what users are **not** currently using AI tools for in order to identify potential market opportunities.

---

## Project Results

The analysis shows that:

- New and experienced coders are using AI tools differently.
- People’s opinions about the usefulness and trustworthiness of current AI tools depend on their experience, job role, and the specific purposes for which they use the tools.

### Key Findings

- **Writing and debugging code** are the most popular AI use cases, but there is clear variation in how different job roles currently use AI tools.
- There are clearly some AI use cases that people are **less interested in**.
- Existing users of AI tools appear to favor and trust these tools more than aspiring users.
- There is **little evidence that a developer’s years of experience affects trust in AI tools**.

---
# 🚀 Installation & Usage

Follow the steps below to set up the project and run it locally.

## 1. Clone the Repository

Clone the project from GitHub:

```bash
git clone <YOUR-REPOSITORY-URL>
cd <YOUR-PROJECT-FOLDER>
```

## 2. Create a Virtual Environment

Create a Python virtual environment:

```bash
python -m venv venv
```

### Activate the Virtual Environment

**Windows:**

```bash
venv\Scripts\activate
```

**macOS / Linux:**

```bash
source venv/bin/activate
```

After activation, you should see `(venv)` at the beginning of your terminal prompt.

## 3. Install Required Libraries

Install all required dependencies from the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

The main libraries used in this project include:

- `pandas`
- `matplotlib`
- `scikit-learn`

## 4. Run the Project

If the project is implemented using Jupyter Notebook:

```bash
jupyter notebook
```

Then open the project notebook and run the cells in order.

If the project contains Python scripts, run the required script using:

```bash
python <script_name>.py
```

## 5. Deactivate the Virtual Environment

When you are finished working with the project:

```bash
deactivate
```

---

## 📦 Requirements

All required Python packages are listed in:

```text
requirements.txt
```

To recreate the project environment on another machine:

```bash
python -m venv venv
```

Activate the environment and then install the dependencies:

```bash
pip install -r requirements.txt
```

---
