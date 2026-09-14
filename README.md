# Finding Customer Segments from Mobile Activity

## 📌 Problem Statement

**AppEcho Insights** is an analytics company focused on mobile user behavior. The company analyzes data on how users interact with their phones and provides insights to mobile phone manufacturers and app developers.

As part of their latest initiative, AppEcho Insights wants to perform **customer segmentation** to better understand mobile user behavior.

The main questions of this project are:

- Are there groups of users who behave in similar ways?
- What types of apps do people use?
  - For example, do some customers use their phones more for social media than others?
- Are there temporal patterns in user behavior?
  - Do users prefer to browse or use their phones at different times of the day?
- Can we identify a more suitable segmentation method or algorithm that can group users based on multiple dimensions of their behavior?

The goal is to use mobile activity data to identify meaningful groups of users with similar behavioral characteristics.

---

## 📂 Data Source

The dataset was originally obtained from the following repository:

- https://github.com/aliannejadi/LSApp

---

## 📖 Data Dictionary

| Column | Description |
|---|---|
| **User ID** | A unique identifier for each user. |
| **Session ID** | Uniquely identifies a user's activity session. |
| **Timestamp** | The date and time of an individual event. |
| **App name** | The name of the application being used. |
| **Event type** | The type of event that took place. Possible values are `Opened`, `Closed`, `User Interaction`, or `Broken`. |

---

## 🎯 Desired Outcomes

The final output of this project is the **definition of user segments**.

For each segment, we want to identify:

- What factors and behavioral characteristics describe the segment.
- Which users belong to each segment.
- How the different segments meaningfully differ from one another.

The objective is not only to create clusters, but also to make the resulting segments understandable and useful by describing each group with meaningful characteristics or **user personas**.

---

## 🛠️ Required Tools

The project uses the following Python libraries:

- **pandas** — Data manipulation and analysis
- **matplotlib** — Data visualization
- **Scikit-learn** — Data preprocessing and machine learning

---

# 🔎 Project Progress

## 1. Data Exploration

We start by exploring the dataset and checking the overall quality of the data.

This includes:

- Looking for missing values.
- Identifying incorrect or inconsistent values.
- Investigating potential outliers.
- Understanding the structure and distribution of the data.

## 2. Feature Investigation

Next, we investigate the dimensions along which users differ.

For example:

- Do some features have significantly more variance than others?
- Which behavioral characteristics vary across customers?
- Are some dimensions unsuitable for segmentation because users are too similar along those dimensions?

If all customers were located in the same geographic area, for example, geography would not be a useful dimension for segmentation.

The goal is to identify the behavioral dimensions that provide meaningful differences between users.

## 3. Data Visualization

We visualize the data across different dimensions to look for obvious groups or patterns.

In large and complex datasets, clearly separated groups may not always be visible. However, visualization can still help identify:

- General patterns in user behavior.
- Unusual or outlier groups.
- Customers whose behavior differs significantly from the rest.

For example, visualization may reveal a small group of customers who spend considerably more time using their phones than other users.

## 4. Selecting Segmentation Dimensions

The next step is specific to the segmentation problem.

We select the dimensions that should be used to segment users based on the results of our exploratory analysis.

The selected dimensions should represent meaningful differences in user behavior.

## 5. Choosing a Clustering Algorithm

Different clustering algorithms are suitable for different types of use cases.

For this project, we use **K-Means clustering** to group users based on their behavioral characteristics.

## 6. Evaluating the Clusters

After clustering, we evaluate the resulting groups by analyzing whether they meaningfully differ from one another.

One important part of this process is assigning **group labels or personas** to each cluster.

If every group can be given a unique and meaningful description, the segmentation is more useful than a solution where multiple segments have essentially the same characteristics.

---

# 🧩 Project Steps

### Data Cleaning

- Drop missing data.
- Drop `"Broken"` events.
- Verify metrics.
- Drop `"Closed"` events.
- Remove exact duplicates.

### Session Analysis

- Calculate session lengths.
- Investigate the distribution of session lengths.
- Investigate when browsing sessions typically start.
- Analyze the distribution of the `"starting hour"`.

### Browsing-Time Segmentation

- Group users into categories based on their most common browsing time.
- Define four groups based on browsing data.

### App Categorization

- Categorize individual apps into broader app categories.
- Update `"Unknown"` values.
- Manually create new app categories where necessary.
- Find the most frequent app category for each user.
- Manually fix users with multiple top categories.

### User-Level Metrics

- Recreate metrics from the initial analysis.
- Add the number of sessions per user.
- Merge all metrics together to create a user-level dataset ready for segmentation.
- Export the user-level data for segmentation.

### Data Transformation

- Transform the data so that all variables are on the same scale.
- Apply **z-score standardization** to continuous variables.

### Clustering

- Choose a clustering algorithm.
- Use **K-Means clustering**.
- Choose the number of clusters using the **Elbow Method**.
- Use the Elbow Method to determine **seven clusters**.
- Perform the clustering.

### Cluster Evaluation

- Evaluate the resulting clusters.
- Analyze the characteristics of each cluster.
- Create meaningful personas for the identified user groups.
- Keep all **seven clusters** as the final segmentation solution.

---

# 📊 Final Segmentation Approach

The final workflow can be summarized as:

**Raw Mobile Activity Data**  
↓  
**Data Cleaning**  
↓  
**Session & User Behavior Analysis**  
↓  
**Browsing-Time Categorization**  
↓  
**App Categorization**  
↓  
**User-Level Feature Engineering**  
↓  
**Feature Scaling / Z-Score Standardization**  
↓  
**K-Means Clustering**  
↓  
**Elbow Method → 7 Clusters**  
↓  
**Cluster Evaluation**  
↓  
**User Personas & Final Segments**

---

# 👤 Cluster Results and User Personas

After applying K-Means clustering and selecting seven clusters using the Elbow Method, the resulting groups were analyzed based on their usage behavior, number of sessions, app categories, session length, and preferred browsing times.

The seven clusters were interpreted as the following user personas:

| Group | Persona Name | Persona Characteristics |
|---:|---|---|
| **0** | **Typical Social Users** | Average number of sessions, mostly social media usage, and activity mostly late in the day and at night. |
| **1** | **Heavy Users** | High number of sessions and apps used, mostly social media, with activity mostly late in the day and at night. |
| **2** | **Casual Users** | Low number of sessions and apps, short usage sessions, and usage mostly for browsing. |
| **3** | **Night Owls** | Users who are active throughout the night, with mostly social media usage. |
| **4** | **Usage Outliers** | Users averaging over 3,600 sessions in total over the observed period, representing unusually high usage. |
| **5** | **Session Length Outliers** | Users with unusually long sessions, averaging almost 10 minutes per usage session. |
| **6** | **Evening Social Users** | Average number of sessions, short usage sessions, mostly social media usage, and activity mostly late in the day. |

## 👥 User Persona Summary

The clustering results reveal several distinct patterns of mobile behavior:

- **Typical Social Users** represent users with average activity levels who primarily use social media during the later hours of the day.
- **Heavy Users** are more active overall, using a larger number of sessions and apps while still showing a strong preference for social media.
- **Casual Users** have relatively low activity levels, short sessions, and primarily use their phones for browsing.
- **Night Owls** are characterized by their nighttime activity and strong social media usage.
- **Usage Outliers** represent users with exceptionally high numbers of sessions compared with the rest of the population.
- **Session Length Outliers** are characterized by unusually long usage sessions, averaging almost 10 minutes per session.
- **Evening Social Users** have an average number of sessions but tend to have short sessions, primarily involving social media during the evening and later hours.

These personas demonstrate that the user population is not homogeneous. The clusters differ not only in **how much users interact with their phones**, but also in **what they use their phones for** and **when they are most active**.

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

# ✅ Final Result

The final result consists of **seven user segments**, where each segment represents a group of users with similar mobile activity and behavioral patterns.

The clusters were evaluated based on their behavioral characteristics, and each group was described using a meaningful **user persona** to make the segmentation easier to interpret and use for business decisions.
