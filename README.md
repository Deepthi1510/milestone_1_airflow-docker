# 🚀 Rocket Launch Data Pipeline using Apache Airflow

## 📌 Project Overview

This project demonstrates a **mini data pipeline using Apache Airflow** to automatically collect information about upcoming rocket launches and download rocket images.

The pipeline fetches data from the **Launch Library 2 API**, extracts rocket image URLs, downloads the images, and stores the metadata and images locally for further analysis.

This project helps understand core **Airflow concepts such as DAGs, scheduling, tasks, and automated workflows**.

---

# 🎯 Problem Statement

Rockets are one of humanity’s greatest engineering achievements, and every rocket launch attracts attention worldwide.

A rocket enthusiast named **John** tracks every rocket launch. However, rocket launch information is scattered across multiple sources. John wants to build an **automated system** that collects information about upcoming rocket launches and stores it in one place.

To start small, John decides to:

* Collect data about upcoming rocket launches
* Extract rocket image URLs
* Download rocket images automatically
* Store the metadata and images locally

---

# 🌐 Data Source

The data is collected from the **Launch Library 2 API**.

Official API:
https://thespacedevs.com/llapi

Endpoint used in this project:

https://ll.thespacedevs.com/2.0.0/launch/upcoming

This API provides data about:

* Upcoming rocket launches
* Launch name
* Launch date
* Rocket details
* Rocket image URLs
* Additional metadata

---

# ⚙️ Pipeline Workflow

The pipeline performs the following steps:

### 1️⃣ Fetch Launch Data

The pipeline fetches upcoming rocket launch data from the API using a request or `curl` command.

Example API call:

```bash
curl -L "https://ll.thespacedevs.com/2.0.0/launch/upcoming"
```

The API returns JSON data containing launch details and image URLs.

---

### 2️⃣ Extract Image URLs

From the API response, the pipeline extracts:

* Launch name
* Launch date
* Rocket image URL

These image URLs are used to download rocket images.

---

### 3️⃣ Download Rocket Images

The pipeline downloads rocket images using the extracted URLs and saves them locally.

The images are stored inside the **images folder**.

---

### 4️⃣ Store Metadata

The complete API response is stored as a JSON file:

`launches.json`

This file contains all launch information for later analysis.

---

# ⏰ Scheduling with Airflow

The pipeline is scheduled using **Apache Airflow DAG scheduling**.

The pipeline runs automatically:

* **Every Monday**
* **Every Wednesday**
* **Every Friday**
* **At 06:00 AM**

Cron Schedule Expression:

```
0 6 * * 1,3,5
```

---

# 🛠 Technologies Used

* Python
* Apache Airflow
* REST API
* JSON
* Bash / Curl
* File system storage

---

# 📂 Project Structure

```
rocket_launch_pipeline/
│
├── download_rocket_launcher.py
├── launches.json
├── images/
│   ├── rocket1.jpg
│   ├── rocket2.jpg
│   └── rocket3.jpg
│
└── README.md
```

---

# ▶️ How to Run the Project

### Step 1 — Install dependencies

```bash
pip install requests
```

---

### Step 2 — Run the Python script

```bash
python download_rocket_launcher.py
```

---

### Step 3 — Check the output

After running the script:

* Rocket images will be stored in the **images folder**
* Launch data will be saved in **launches.json**

---

