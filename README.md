# Smart Query Routing System using n8n + LLM + Sentiment Analysis

Automates student query handling for large organizations like **Innomatics Research Labs** by analyzing each query, identifying its urgency, categorizing it by department, and sending it directly to the concerned Head of Department (HOD) via email.

---

## 🔹 Problem Statement

Students from multiple branches often raise queries related to academics, access issues, certifications, or administrative concerns.
Manually reviewing and routing these queries is **time-consuming, inefficient, and prone to delays**.

This project **automates the process** by using AI-driven sentiment analysis, department classification, and automated email routing.

---

## 🔹 Objective

Build an AI-driven Query Routing System using **n8n workflow automation** that:

1. Collects student queries from a **Google Form**.
2. Detects the **urgency** of the query using a **Sentiment Analysis Node**.
3. Classifies the query into the **correct department** using an **LLM Node**.
4. Routes the query automatically to the **respective HOD via email**.

---

## 🔹 Tools & Nodes Used

| Node                           | Purpose                                           |
| ------------------------------ | ------------------------------------------------- |
| **Google Sheet Node**          | Collects Google Form responses                    |
| **Sentiment Analysis Node**    | Detects whether the query is `Urgent` or `Normal` |
| **LLM Node (Basic LLM Chain)** | Classifies queries into the correct department    |
| **Switch / IF Node**           | Routes queries to corresponding department emails |
| **Email Node**                 | Sends structured query details to the department  |

---

## 🏫 Available Departments (Categories)

* Technical Doubt
* WiFi Issue
* Certification
* NASSCOM
* Batch Change
* Teaching Methodology
* LMS Access
* Discord Access
* Payment Issue
* Room Allocation
* Placement
* Resume Review
* Revoke Access
* Live Class Access
* Quiz Related
* Recording Video Access
* Assignments
* Tasks

---

## 🔹 Department Routing Configuration

| Category            | Department            | Email ID                                                      |
| ------------------- | --------------------- | ------------------------------------------------------------- |
| WiFi Issue          | IT Support            | [it_support@innomatics.in](mailto:it_support@innomatics.in)   |
| Placement           | Placement Cell        | [placement@innomatics.in](mailto:placement@innomatics.in)     |
| Certification       | Admin Department      | [admin@innomatics.in](mailto:admin@innomatics.in)             |
| Batch Change        | Academic Coordinator  | [academic@innomatics.in](mailto:academic@innomatics.in)       |
| Technical Doubt     | Trainer / Mentor      | [trainer@innomatics.in](mailto:trainer@innomatics.in)         |
| LMS Access          | LMS Technical Support | [lms_support@innomatics.in](mailto:lms_support@innomatics.in) |
| Payment Issue       | Accounts Department   | [accounts@innomatics.in](mailto:accounts@innomatics.in)       |
| Assignments / Tasks | Training Department   | [training@innomatics.in](mailto:training@innomatics.in)       |

> **Note:** Use your own or friends’ email IDs for testing.

---

## 🔹 Workflow Steps

### 1️⃣ Query Submission (Google Form)

**Fields captured:**

* Name
* Enrollment ID
* Batch Number
* Branch (Dropdown: HYD_JNTU, HYD_LB_Nagar, Pune, Bangalore)
* Query Text

### 2️⃣ Google Sheet Trigger

* Triggers the n8n workflow automatically upon new entry.

### 3️⃣ Sentiment Analysis Node

* Detects query urgency: **Urgent / Normal**

### 4️⃣ Basic LLM Chain Node

* **System Prompt:** Describes all departments and their roles.
* **User Prompt:** Provides query text, student details, and sentiment.
* Outputs predicted department category.

### 5️⃣ Switch / IF Node

* Matches the LLM-predicted category to the corresponding department email.

### 6️⃣ Email Node

* Sends automated email to the department head containing query details.

---

## 🔹 Example Output Email

**Subject:** Urgent Query - LMS Access (HYD_JNTU)
**Body:**

```
Dear [Department Head],

A new student query has been received.

🧍 Name: Vangapandu Lakshmi  
🆔 Enrollment ID: DS2456  
🏫 Branch: HYD_JNTU  
📊 Sentiment: Urgent  
📝 Query: “I can’t access my LMS account since yesterday.”

Please look into this issue at the earliest.

Thank You,  
Innomatics Query Routing System
```

---

## 🔹 Example Classification Flow

**Student Query:**
“My LMS login is not working since morning.”

**Sentiment Node Output:**
`Urgent`

**LLM Node Output:**

```json
{
  "sentiment": "urgent",
  "category": "LMS Access"
}
```

**Routing Result:**
📩 Email automatically sent to → `lms_support@innomatics.in`

---

## 🔹 Folder Structure

```
Smart-Query-Routing-n8n-LLM-SentimentAnalysis/
│
├── workflows/
│   └── query_routing_workflow.json   # n8n exported workflow
│
├── docs/
│   └── screenshots/                  # Workflow screenshots
│
├── README.md
└── LICENSE
```

---

## 🔹 Tech Stack

* Google Sheets
* n8n Workflow Automation
* OpenAI / Google LLM
* Sentiment Analysis Node
* Switch & Email Nodes

---

## 🔹 LinkedIn Profile

[Charitha Vanga](https://www.linkedin.com/in/charitha-vanga)

---

## 🔹 License

MIT License (open-source and free to use)

---
