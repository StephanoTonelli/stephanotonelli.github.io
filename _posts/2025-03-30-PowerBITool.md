<!-- ---
title: "TCO tool for Vehicles"
layout: single
author_profile: false
image: \assets\icon-python.png
categories:
  - Programming
  - Cloud
  - API
  - DevOps
tags:
  - Python
  - FastAPI
  - SQL
  - Azure
  - Docker
  - Jupyter
  - Performance Testing
---

<h2>Project Overview</h2>
<p style="font-size:0.8em">
The <strong>Smart Truck Rating API</strong> is a robust cloud-based solution that evaluates commercial trucks for environmental and operational efficiency using predefined metrics. It provides a RESTful API for scoring and recommendations, integrated with SQL-based data logging, tested using Jupyter Notebooks, and deployed with Docker on Azure Container Apps.
</p>

<p style="font-size:0.8em"><strong>Technology:</strong> FastAPI, Python, SQLAlchemy, SQLite/SQL Server, Pandas, Docker, Azure Container Apps</p>
<p style="font-size:0.8em"><strong>Testing Tools:</strong> Jupyter Notebook, Pandas, Linux (ApacheBench)</p>

<h2>Key Features</h2>
<ul style="font-size:0.8em">
    <li>API authentication using API keys and timestamp headers.</li>
    <li>Custom rating logic based on vehicle attributes (pollution standard, transmission, aerodynamics, etc.).</li>
    <li>Dynamic score calculations with detailed recommendations.</li>
    <li>Persistent logging of all requests in an Azure-hosted SQL database.</li>
    <li>Batch testing with expected output comparison in Jupyter Notebook.</li>
    <li>Load testing via command-line with ApacheBench for performance analysis.</li>
</ul>

<h2>Architecture & Components</h2>
<pre style="font-size:0.8em">
SmartTruckAPI/
│── app/
│   │── main.py (FastAPI entry point)
│   │── scoring_logic.py (Custom business rules)
│   │── models.py (SQLAlchemy models)
│   │── middleware.py (Logging middleware)
│   │── database.py (DB connection logic)
│── tests/
│   │── test_runner.ipynb (Jupyter notebook for batch testing)
│── Dockerfile (API containerization)
│── requirements.txt
</pre>

<h2>Example Code</h2>
<pre style="font-size:0.8em">
# API call via requests in Jupyter
response = requests.post(
    url, json=payload,
    headers={"x-api-key": key, "timestamp": timestamp})
result = response.json()
</pre>

<h2>Performance Insights</h2>
<ul style="font-size:0.8em">
    <li><strong>Response Speed:</strong> API optimized with async routes and Uvicorn server.</li>
    <li><strong>Scaling:</strong> Container deployed to Azure with automated load balancing.</li>
    <li><strong>Logging:</strong> Every request tracked for debugging and analytics.</li>
</ul>

<h2>Project Link</h2>
<p style="font-size:0.8em"><a href="https://github.com/StephanoTonelli/SmartTruckRating" target="_blank">GitHub Repository</a></p> -->
