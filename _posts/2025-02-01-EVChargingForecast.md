---
title: "EV Charging Infrastructure Forecast"
layout: single
author_profile: false
image: \assets\icon-microsoft-excel.png
categories:
  - Data Analysis
  - Forecasting
  - Business
  - Programming
tags:
  - Excel
  - Data Analysis
  - EV Infrastructure
  - Forecasting
  - Queensland
---

<h2>Project Overview</h2>
<p style="font-size:0.8em">
This project involved building a comprehensive forecast model to predict future electric vehicle (EV) charging infrastructure needs for a major transportation hub client in Queensland. Working with Mov3ment, I analyzed vehicle visitation patterns, EV adoption trends, and population growth data to help the client plan their charging infrastructure upgrades over the coming years. The analysis combined multiple government datasets, industry reports, and demographic projections to create actionable forecasts.
</p>

<p style="font-size:0.8em"><strong>Technology:</strong> Microsoft Excel (Power Query, pivot tables, data modeling, forecasting)</p>
<p style="font-size:0.8em"><strong>Data Sources:</strong> Queensland vehicle registration data, FCAI sales reports, Energex EV insights, ABS population projections</p>

<h2>The Challenge</h2>
<p style="font-size:0.8em">
The client needed to understand how many EV charging stations they would need in the future to serve their visitors. This wasn't just about looking at current EV numbers. It required forecasting how many electric vehicles would be visiting their facility in 5, 10, or even 15 years, and then translating that into concrete infrastructure requirements.
</p>

<p style="font-size:0.8em">
The tricky part was combining different data sources that don't always line up perfectly. Vehicle registration data by postcode, statewide EV adoption trends, population growth projections, and historical sales data all had to come together to paint a realistic picture of the future.
</p>

<h2>The Approach</h2>
<p style="font-size:0.8em">
I built the forecast model in Excel, which gave the client flexibility to adjust assumptions and see how different scenarios would affect their infrastructure needs. The analysis had several key components:
</p>

<h3 style="font-size:0.9em">1. Understanding Current Visitation Patterns</h3>
<p style="font-size:0.8em">
I started by analyzing where the client's visitors were coming from using postcode-level data. This geographic distribution was important because EV adoption rates vary significantly by region. Inner-city areas tend to have higher EV uptake than regional areas, so understanding the visitor profile was crucial.
</p>

<h3 style="font-size:0.9em">2. Analyzing EV Adoption Trends</h3>
<p style="font-size:0.8em">
Using data from the Federal Chamber of Automotive Industries (FCAI) and Queensland vehicle registration records, I tracked how EV adoption has been growing over time. The data showed both the overall trend and how it's accelerating. I looked at sales by fuel type to understand not just battery electric vehicles (BEVs), but also plug-in hybrids (PHEVs) that would need charging infrastructure.
</p>

<h3 style="font-size:0.9em">3. Building the Forecast Model</h3>
<p style="font-size:0.8em">
The core of the model combined several factors:
</p>
<ul style="font-size:0.8em">
    <li><strong>Population growth projections</strong> for South East Queensland (SEQ) by local government area</li>
    <li><strong>Historical EV adoption curves</strong> showing how quickly electric vehicles are being purchased</li>
    <li><strong>Fleet composition changes</strong> based on vehicle sales trends and vehicle turnover rates</li>
    <li><strong>Visitor patterns</strong> specific to the client's facility</li>
</ul>

<p style="font-size:0.8em">
I created different scenarios (conservative, moderate, aggressive) to account for uncertainty in how fast EV adoption might accelerate. This gave the client a range of possible outcomes rather than a single prediction.
</p>

<h3 style="font-size:0.9em">4. Translating Vehicle Numbers to Infrastructure Needs</h3>
<p style="font-size:0.8em">
Once I had forecasts for how many EVs would be visiting the facility, I worked backward to calculate charging infrastructure requirements. This involved considering factors like:
</p>
<ul style="font-size:0.8em">
    <li>Average dwell time (how long vehicles stay)</li>
    <li>Charging speed requirements (fast charging vs. slower charging)</li>
    <li>Peak demand periods</li>
    <li>Buffer capacity for growth and unexpected demand</li>
</ul>

<h2>Data Sources</h2>
<p style="font-size:0.8em">
The analysis drew on multiple datasets to build a comprehensive picture:
</p>

<ul style="font-size:0.8em">
    <li><strong>Queensland Vehicle Registrations:</strong> Current fleet composition and registration trends by postcode</li>
    <li><strong>FCAI Sales Data:</strong> New vehicle sales broken down by fuel type (petrol, diesel, hybrid, PHEV, BEV)</li>
    <li><strong>Energex EV Insights:</strong> Queensland-specific EV adoption data and grid connection information</li>
    <li><strong>ABS Population Projections:</strong> South East Queensland population growth by Greater Capital City Statistical Area (GCCSA)</li>
    <li><strong>Historical Sales Trends:</strong> Multi-year data showing how fuel type preferences have evolved</li>
    <li><strong>Postcode Registration Data:</strong> Geographic distribution of current vehicle registrations</li>
</ul>

<h2>Technical Implementation</h2>

<h3 style="font-size:0.9em">Excel as the Analysis Platform</h3>
<p style="font-size:0.8em">
I used Excel for this project because it's accessible to the client team for future updates and scenario testing. The workbook includes:
</p>

<ul style="font-size:0.8em">
    <li><strong>Power Query connections</strong> to clean and transform the raw data sources</li>
    <li><strong>Data modeling</strong> to link population, adoption rates, and visitation patterns</li>
    <li><strong>Scenario analysis tables</strong> allowing the client to adjust key assumptions</li>
    <li><strong>Dynamic charts</strong> that update based on scenario selections</li>
    <li><strong>Summary dashboard</strong> showing infrastructure needs over time</li>
</ul>

<h3 style="font-size:0.9em">Forecast Methodology</h3>
<p style="font-size:0.8em">
The forecasting approach combined:
</p>
<ul style="font-size:0.8em">
    <li><strong>Trend analysis:</strong> Extrapolating historical EV sales growth patterns</li>
    <li><strong>Adoption curve modeling:</strong> Using S-curve patterns typical of technology adoption</li>
    <li><strong>Cohort analysis:</strong> Tracking how different vehicle age groups transition to EVs</li>
    <li><strong>Geographic weighting:</strong> Adjusting for regional differences in EV uptake</li>
</ul>

<h2>Key Findings</h2>
<p style="font-size:0.8em">
The analysis revealed several important insights:
</p>

<ul style="font-size:0.8em">
    <li>EV adoption in Queensland is accelerating faster than many earlier projections suggested</li>
    <li>The visitor profile for this client skews toward regions with higher EV adoption rates</li>
    <li>Infrastructure needs grow non-linearly (small increases in EV percentage can create large increases in charging demand)</li>
    <li>Planning for fast-charging capability is more important than initially expected</li>
    <li>Peak demand periods create multiplier effects on required infrastructure</li>
</ul>

<h2>What I Learned</h2>
<p style="font-size:0.8em">
This project taught me several things about working with real-world forecasting challenges:
</p>

<ul style="font-size:0.8em">
    <li><strong>Data integration is messy:</strong> Government datasets, industry reports, and demographic projections all use different formats, time periods, and geographic boundaries. Getting them to work together takes time.</li>
    <li><strong>Uncertainty is part of the answer:</strong> Providing scenario ranges is more useful than trying to predict a single "correct" future. The client needs to see the range of possibilities.</li>
    <li><strong>Make it accessible:</strong> Building the model in Excel meant the client could understand and modify it themselves. That's more valuable than a complex model they can't work with.</li>
    <li><strong>Domain knowledge matters:</strong> Understanding how EV adoption works, what drives infrastructure needs, and how visitor behavior impacts charging demand was just as important as the technical analysis.</li>
    <li><strong>Visuals tell the story:</strong> Clear charts showing how infrastructure needs grow over time made the forecast much more actionable than tables of numbers.</li>
</ul>

<p style="font-size:0.8em">
This was also my first major forecasting project using multiple data sources. I learned a lot about how to combine datasets that don't perfectly align and how to communicate uncertainty in a way that helps decision-making rather than paralyzing it.
</p>

<h2>Practical Applications</h2>
<p style="font-size:0.8em">
The forecast helps the client:
</p>

<ul style="font-size:0.8em">
    <li>Plan capital expenditure for charging infrastructure over multiple years</li>
    <li>Time infrastructure upgrades to match projected demand growth</li>
    <li>Avoid both over-investment (installing too much too soon) and under-investment (not keeping pace with demand)</li>
    <li>Communicate infrastructure plans to stakeholders with data-backed projections</li>
    <li>Respond to RFPs and planning requirements with quantitative analysis</li>
</ul>

<h2>Project Context</h2>
<p style="font-size:0.8em">
This work was completed for Mov3ment as part of their sustainability consulting services. The client needed to transition from general awareness that "EVs are coming" to concrete plans for infrastructure investment. The forecast provided the quantitative foundation for those decisions.
</p>

