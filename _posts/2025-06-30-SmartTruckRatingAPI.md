---
title: "Smart Truck Rating API"
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
The <strong>Smart Truck Rating API</strong> is a production REST API developed for Mov3ment's RateYourTruck platform. It evaluates commercial trucks for environmental and operational efficiency based on a comprehensive rating scheme created by Mark Gjerek. The API accepts detailed vehicle specifications and returns star ratings along with specific recommendations for improvement. Deployed on Azure Container Apps, it serves real-time rating calculations for fleet operators across Australia.
</p>

<p style="font-size:0.8em"><strong>Technology:</strong> Python 3.11, FastAPI, SQLAlchemy, SQLite, Pydantic, Uvicorn, Docker, Azure Container Apps</p>
<p style="font-size:0.8em"><strong>Testing Tools:</strong> Jupyter Notebook, Pandas for test case management</p>

<h2>The Challenge</h2>
<p style="font-size:0.8em">
There's been no standard way to compare truck fuel efficiency or emissions in Australia. The rating scheme addresses this by providing operators a simple star rating that rewards decisions on features and equipment that reduce energy use and emissions, not just the truck brand or powertrain. My role was translating this sophisticated rating logic into a flexible, maintainable API that could handle 40+ vehicle configuration parameters and provide actionable advice.
</p>

<h2>Key Features</h2>
<ul style="font-size:0.8em">
    <li>API key authentication with expiration tracking and client name validation.</li>
    <li>Timestamp header validation for additional request security.</li>
    <li>Dynamic scoring based on database-configured weights (pollution standards, efficiency features, aerodynamics, smart systems).</li>
    <li>Star rating generation with percentage breakdowns across categories.</li>
    <li>Intelligent advice system prioritizing retrofits over new vehicle purchases.</li>
    <li>Request logging to SQLite database via SQLAlchemy for audit trail.</li>
    <li>Comprehensive validation of 40+ input fields using Pydantic schemas.</li>
    <li>Health check endpoint for availability monitoring.</li>
</ul>

<h2>Architecture & Components</h2>
<pre style="font-size:0.8em">
SmartTruckRating/
├── app/
│   ├── main.py                   # FastAPI app setup and middleware
│   ├── scoring_logic.py          # Core logic for vehicle scoring
│   ├── rating_logic.py           # Star rating conversion
│   ├── advice_gen.py             # Recommendation generation
│   ├── schemas.py                # Pydantic models for validation
│   ├── authentication.py         # API key and timestamp validation
│   ├── database.py               # SQLAlchemy DB setup
│   ├── model_log.py              # Request logging model
│   ├── routers/
│   │   └── rating.py             # Rating endpoints
│   └── data/                     # (API keys managed in database)
├── tests/
│   ├── test_cases.csv            # Test scenarios
│   └── run_tests.ipynb           # Jupyter notebook for validation
├── SQL_Database/                 # Database schema and setup
├── Dockerfile                    # Container build recipe
├── dev_requirements.txt          # Local development dependencies
└── container_requirements.txt    # Production container dependencies
</pre>

<h2>Design Decisions</h2>

<h3 style="font-size:0.9em">Database-Driven Configuration</h3>
<p style="font-size:0.8em">
One of my favorite design choices was making the scoring logic configurable through database tables. I started by organizing all the scoring variables in CSV format during development to get a clear view of the weights and relationships, then created SQL tables to store these variables for production. This allows the operations team to update scoring weights, add new features, or adjust rating thresholds through direct database updates without code changes. It's practical and maintainable.
</p>

<h3 style="font-size:0.9em">Modular Business Logic</h3>
<p style="font-size:0.8em">
The scoring, rating, and advice generation are separated into distinct modules. This makes it easy to test individual components and modify one aspect without affecting others.
</p>

<h3 style="font-size:0.9em">Request Validation</h3>
<p style="font-size:0.8em">
With 40+ fields in the request body, Pydantic's automatic validation prevents bad data from reaching the business logic. If a field is missing or the wrong type, the API returns a clear error before any processing happens.
</p>

<h2>Example API Request</h2>
<pre style="font-size:0.8em">
import requests
from datetime import datetime

url = "https://api.rateyourtruck.com.au/rating/single"
headers = {
    "x-api-key": "your-api-key",
    "timestamp": datetime.utcnow().isoformat() + "Z",
    "Content-Type": "application/json"
}

payload = {
    "user_name": "Fleet Manager",
    "user_email": "manager@example.com",
    "duty_cycle": "Mostly Urban",
    "vehicle_type": "Rigid (Urban or regional)",
    "make": "Volvo",
    "model": "FE",
    "yom": 2025,
    "pollution": "Euro VI",
    "transmission": "Automated manual transmission",
    "eco_mode": True,
    "lrr": True,
    "telematics": True,
    # ... 30+ more configuration options
}

response = requests.post(url, json=payload, headers=headers)
result = response.json()

print(f"Rating: {result['rating']} stars")
print(f"Pollution Score: {result['percent_pollution']}%")
print(f"Top Advice: {result['advice']['Advice 1']}")
</pre>

<h2>Deployment & Cloud Infrastructure</h2>
<p style="font-size:0.8em">
The API is containerized with Docker and deployed to <strong>Azure Container Apps</strong>. This was my first time working with Azure cloud services, so it was a good learning experience. I explored Azure's container orchestration, environment variables management, networking configuration, and monitoring capabilities. Azure Container Apps made it straightforward to deploy without managing the underlying infrastructure, and the API scales automatically based on load.
</p>

<h3 style="font-size:0.9em">Deployment Process</h3>
<pre style="font-size:0.8em">
# Build container image
docker build -t smarttruckrating -f Dockerfile .

# Deploy to Azure Container Apps
# (via Azure Portal or Azure CLI)
az containerapp create \
  --name smarttruckrating \
  --resource-group mov3ment-rg \
  --image smarttruckrating:latest \
  --environment production
</pre>

<h2>Testing Strategy</h2>
<p style="font-size:0.8em">
I built a comprehensive test suite using Jupyter Notebooks. Test cases are defined in CSV files with expected outputs, making it easy to verify that scoring logic changes don't break existing behavior. The notebook loads test scenarios, calls the API, and compares actual vs. expected results with detailed reporting.
</p>

<h2>Performance Insights</h2>
<ul style="font-size:0.8em">
    <li><strong>Response Time:</strong> API optimized with async routes and Uvicorn ASGI server for fast response times.</li>
    <li><strong>Validation Speed:</strong> Pydantic's compiled validators handle 40+ field validation efficiently.</li>
    <li><strong>Scaling:</strong> Azure Container Apps provides automatic horizontal scaling based on HTTP traffic.</li>
    <li><strong>Logging:</strong> Every request tracked with timestamp, client name, and response data for debugging and analytics.</li>
    <li><strong>Security:</strong> Multi-layer authentication (API keys + timestamp validation) prevents unauthorized access.</li>
</ul>

<h2>Skills I Practiced</h2>
<p style="font-size:0.8em">
This project gave me hands-on experience with several technical areas:
</p>
<ul style="font-size:0.8em">
    <li><strong>API Design:</strong> Structuring endpoints, choosing HTTP methods, designing clear request/response schemas.</li>
    <li><strong>Security Implementation:</strong> API key authentication, timestamp validation, keeping secrets out of code.</li>
    <li><strong>Cloud Deployment:</strong> Working with Azure Container Apps, managing container images, configuring cloud resources.</li>
    <li><strong>Azure Platform:</strong> Container services, networking, environment management, and monitoring.</li>
    <li><strong>Data Modeling:</strong> Translating complex rating logic into flexible, maintainable code.</li>
</ul>
<p style="font-size:0.8em">
Building production APIs and deploying to cloud infrastructure was relatively new territory for me. My mechanical engineering background helped me understand the vehicle characteristics and efficiency factors, but the API development and cloud deployment side required focus and effort. FastAPI's excellent documentation and Azure's straightforward Container Apps service made it manageable.
</p>

<h2>Practical Applications</h2>
<p style="font-size:0.8em">
The RateYourTruck platform (powered by this API) helps:
</p>
<ul style="font-size:0.8em">
    <li>Fleet managers assess their vehicles' environmental impact.</li>
    <li>Companies evaluate new vehicle purchases with objective data.</li>
    <li>Operators prioritize efficiency upgrades and retrofits.</li>
    <li>Organizations meet environmental reporting requirements.</li>
    <li>Supply chain partners demonstrate fleet improvements to customers.</li>
</ul>

<h2>Simplified Example Repository</h2>
<p style="font-size:0.8em">
I created a public example repository that demonstrates similar architectural patterns with simplified logic: <a href="https://github.com/StephanoTonelli/FastAPI_VehicleRating" target="_blank">FastAPI_VehicleRating</a>
</p>
<p style="font-size:0.8em">
That repo uses basic scoring based on vehicle age, mileage, and engine size (completely made-up logic), but demonstrates the same patterns:
</p>
<ul style="font-size:0.8em">
    <li>FastAPI routers and Pydantic schemas</li>
    <li>CSV-based configuration (the example uses CSV files for simplicity)</li>
    <li>API key authentication</li>
    <li>Request logging with SQLAlchemy</li>
    <li>Docker deployment</li>
</ul>
<p style="font-size:0.8em">
The actual Smart Truck Rating API uses database tables for all configuration (scoring variables, API keys, rating thresholds) and a far more sophisticated scoring model with dozens of weighted features across multiple categories, but the fundamental structure is the same.
</p>

<h2>Project Links</h2>
<p style="font-size:0.8em">
<a href="https://github.com/StephanoTonelli/FastAPI_VehicleRating" target="_blank">Simplified Example Repository</a><br>
<a href="https://www.rateyourtruck.com.au" target="_blank">RateYourTruck Platform</a>
</p>
