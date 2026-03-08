#  Welcome to CodeBook – Your Data Science Internship Begins!

## Introduction
Congratulations!

You have just been hired as a **Data Scientist Intern** at **CodeBook – The Social Media for Coders**.

This Delhi-based company is offering you a **₹10 LPA job** if you successfully complete this **1-month internship**. But before you get there, you must prove your skills using **only Python** — **no Pandas, NumPy, or fancy libraries!**

Your manager **Puneet Kumar** has assigned you your first task:
**Analyzing a data dump of CodeBook users using pure Python.**

Your job is to **load and explore the data to understand its structure.**

---

# Task 1: Load the User Data

Your manager has given you a **dataset** containing information about:

- CodeBook **users**
- Their **connections (friends)**
- The **pages they have liked**

This is how the data looks (**JSON format**):

```json
{
    "users": [
        {"id": 1, "name": "Amit", "friends": [2, 3], "liked_pages": [101]},
        {"id": 2, "name": "Priya", "friends": [1, 4], "liked_pages": [102]},
        {"id": 3, "name": "Rahul", "friends": [1], "liked_pages": [101, 103]},
        {"id": 4, "name": "Sara", "friends": [2], "liked_pages": [104]}
    ],
    "pages": [
        {"id": 101, "name": "Python Developers"},
        {"id": 102, "name": "Data Science Enthusiasts"},
        {"id": 103, "name": "AI & ML Community"},
        {"id": 104, "name": "Web Dev Hub"}
    ]
}
```

###  Understanding the Data Structure

The dataset contains **three main components**:

**1️⃣ Users**
- Each user has:
  - **ID**
  - **Name**
  - A list of **friends** (by their IDs)
  - A list of **liked pages** (by their IDs)

**2️⃣ Pages**
- Each page has:
  - **ID**
  - **Name**

**3️⃣ Connections**
- Users can:
  - Have **multiple friends**
  - Like **multiple pages**

---

# Task 2: Read and Display the Data using Python

Your goal is to **load this data and display it in a structured format** using Python.

Use **Python's built-in modules only**.

### Steps

1️⃣ Save the JSON data in a file called:

```
codebook_data.json
```

2️⃣ Read the JSON file using Python.

3️⃣ Print:
- **User details**
- Their **friends/connections**

4️⃣ Print the **available pages**.

---

**Goal:**
Understand how to **read JSON data**, **parse it**, and **explore structured data using pure Python**.


# Cleaning and Structuring the Data
## Introduction
- Your manager is impressed with your progress but points out that the data is messy. Before we can analyze it effectively, we need to clean and structure the data properly.

#### Your task is to:

- Handle missing values
- Remove duplicate or inconsistent data
- Standardize the data format
- Let's get started!

# Task 1: Identify Issues in the Data
Your manager provides you with an example dataset where some records are incomplete or incorrect. Here’s an example:

```json
{
    "users": [
        {"id": 1, "name": "Amit", "friends": [2, 3], "liked_pages": [101]},
        {"id": 2, "name": "Priya", "friends": [1, 4], "liked_pages": [102]},
        {"id": 3, "name": "Rahul", "friends": [1], "liked_pages": [101, 103]},
        {"id": 4, "name": "Sara", "friends": [2], "liked_pages": [104]}
    ],
    "pages": [
        {"id": 101, "name": "Python Developers"},
        {"id": 102, "name": "Data Science Enthusiasts"},
        {"id": 103, "name": "AI & ML Community"},
        {"id": 104, "name": "Web Dev Hub"}
    ]
}
```

## Problems:
- User ID 3 has an empty name.
- User ID 4 has a duplicate friend entry.
- User ID 5 has no connections or liked pages (inactive user).
- The pages list contains duplicate page IDs.
# Task 2: Clean the Data
### We will:

- Remove users with missing names.
- Remove duplicate friend entries.
- Remove inactive users (users with no friends and no liked pages).
- Deduplicate pages based on IDs.

# Finding "People You May Know"
Now that our data is cleaned and structured, your manager assigns you a new task: Build a 'People You May Know' feature!

In social networks, this feature helps users connect with others by suggesting friends based on mutual connections. Your job is to analyze mutual friends and recommend potential connections.

# Task 1: Understand the Logic
## How 'People You May Know' Works:
- If User A and User B are not friends but have mutual friends, we suggest User B to User A and vice versa.
- More mutual friends = higher priority recommendation.
### Example:

- Amit (ID: 1) is friends with Priya (ID: 2) and Rahul (ID: 3).
- Priya (ID: 2) is friends with Sara (ID: 4).
- Amit is not directly friends with Sara, but they share Priya as a mutual friend.
- Suggest Sara to Amit as "People You May Know".
But there are cases where we will have more than one "People You May Know". In those cases, greater the number of mutual friends, higher the probability that the user might know the person we are recommending.

# Task 2: Implement the Algorithm
We'll create a function that:

- Finds all friends of a given user.
- Identifies mutual friends between non-friends.
- Ranks recommendations by the number of mutual friends.


# Finding "Pages You Might Like"
We've officially reached the final milestone of our first data science project at CodeBook – The Social Media for Coders. After cleaning messy data and building features like People You May Know, it's time to launch our last feature: Pages You Might Like.

# Why This Matters
- In real-world social networks, content discovery keeps users engaged. This feature simulates that experience using nothing but pure Python, showing how even simple logic can power impactful insights. So now the situation is that your manager is impressed with your 'People You May Know' feature and now assigns you a new challenge: Recommend pages that users might like!

- On social media platforms, users interact with pages by liking, following, or engaging with posts. The goal is to analyze these interactions and suggest relevant pages based on user behavior.

# Task 1: Understanding the Recommendation Logic
## How 'Pages You Might Like' Works:
- Users engage with pages (like, comment, share, etc.).
- If two users have interacted with similar pages, they are likely to have common interests.
- For the sake of this implementation, we consider liking a page as an interaction
- Pages followed by similar users should be recommended.
### Example:

- Amit (ID: 1) likes Python Hub (Page ID: 101) and AI World (Page ID: 102).
- Priya (ID: 2) likes AI World (Page ID: 102) and Data Science Daily (Page ID: 103).
- Since Amit and Priya both like AI World (102), we suggest Data Science Daily (103) to Amit and Python Hub (101) to Priya.
### What we are using here is called collaborative filtering:

"If two people like the same thing, maybe they’ll like other things each one likes too."

This is a basic form of a real-world recommendation engine, and our task is to implement it in pure Python. Let's Go!

# Task 2: Implement the Algorithm
We'll create a function that:

- Maps users to pages they have interacted with.
- Identifies pages liked by users with similar interests.
- Ranks recommendations based on common interactions.
