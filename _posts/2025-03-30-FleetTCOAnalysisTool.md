---
title: "Fleet TCO Tool: Lessons in Constraints and Expectations"
layout: single
author_profile: false
image: \assets\icon-power-bi.png
categories:
  - Data Analysis
  - Programming
  - Project Management
  - Lessons Learned
tags:
  - Power BI
  - Excel
  - Project Management
  - Database Design
  - User Experience
---

<h2>Project Overview</h2>
<p style="font-size:0.8em">
I built a Total Cost of Ownership analysis tool for Mov3ment's fleet transition projects, but this is the story of how the project evolved, the platform limitations I hit, and the hard lessons I learned about aligning expectations early. The tool went through multiple iterations from August 2024 to March 2025, and the final version looks very different from what we originally envisioned. This project taught me as much about project management as it did about Power BI development.
</p>

<p style="font-size:0.8em"><strong>Technology:</strong> Microsoft Power BI, Excel (VBA), Miro (database design)</p>
<p style="font-size:0.8em"><strong>Timeline:</strong> August 2024 - March 2025 (8+ iterations)</p>
<p style="font-size:0.8em"><strong>Key Lesson:</strong> Platform constraints and clear expectations matter more than fancy features</p>

<h2>The Challenge</h2>
<p style="font-size:0.8em">
Mov3ment needed a tool to analyze vehicle fleets and calculate Total Cost of Ownership. Straightforward enough, right? But the real challenge became managing what the team wanted versus what Power BI could actually deliver.
</p>

<p style="font-size:0.8em">
The initial vision was ambitious. The team wanted maximum flexibility to slice data every possible way, create custom reports on the fly, and adjust parameters for dozens of different scenarios. As I got deeper into development, I kept hitting Power BI's limitations. The platform is powerful for visualization and analysis, but it's not a flexible application development environment.
</p>

<p style="font-size:0.8em">
Looking back, the bigger challenge wasn't technical. It was about understanding constraints early, communicating them clearly, and aligning everyone's expectations before building too much.
</p>

<h2>Designing from Scratch</h2>
<p style="font-size:0.8em">
Before writing a single line of code or creating any Power BI visuals, I spent time in Miro designing the database structure. This turned out to be one of the best decisions for the project.
</p>

<p style="font-size:0.8em">
I created a visual map showing:
</p>
<ul style="font-size:0.8em">
    <li>All the data tables and their relationships (fact tables, dimension tables, lookup tables)</li>
    <li>How information flows between different parts of the analysis</li>
    <li>Where calculations happen and what feeds into them</li>
    <li>What data comes from the Excel database versus what's calculated in Power BI</li>
</ul>

<p style="font-size:0.8em">
Having this map made development so much easier. When I needed to add a new feature or change something, I could look at the diagram and immediately see what would be affected. It also helped me explain the structure to the team when they had questions about why certain things worked the way they did.
</p>

<p style="font-size:0.8em">
The database itself is entirely custom. There was no existing structure to follow, so I had to figure out what data points would actually be useful for analyzing fleets. This meant a lot of back and forth with the team, trying different structures, and refining based on what worked in practice.
</p>

<h2>Custom Navigation and User Experience</h2>
<p style="font-size:0.8em">
One of the first things I decided was that the tool shouldn't look like a typical Power BI dashboard. The team wasn't going to be Power BI experts, so having them navigate tabs and built-in Power BI controls felt wrong.
</p>

<p style="font-size:0.8em">
Instead, I built a custom menu system using buttons. When you open the tool, you see a clean interface with clear navigation options. Click a button, and it takes you to the analysis you need. No hunting through tabs, no confusion about what's available.
</p>

<p style="font-size:0.8em">
This meant:
</p>
<ul style="font-size:0.8em">
    <li>Designing button layouts and navigation flows</li>
    <li>Using Power BI bookmarks and page navigation actions</li>
    <li>Creating a consistent visual design across all screens</li>
    <li>Making sure the interface felt intuitive, not like a dashboard</li>
</ul>

<p style="font-size:0.8em">
The custom navigation made the tool feel more like an application than a report. It also meant I could control exactly what the user saw at each step, which helped reduce confusion.
</p>

<h2>Hitting Platform Limitations</h2>
<p style="font-size:0.8em">
Here's where things got challenging. Power BI is excellent for what it's designed to do, but the team kept asking for features that pushed beyond those boundaries.
</p>

<p style="font-size:0.8em">
Some examples:
</p>
<ul style="font-size:0.8em">
    <li><strong>Dynamic parameter inputs:</strong> Users wanted to adjust dozens of parameters on the fly. Power BI doesn't handle this elegantly. You can do it, but it gets messy fast.</li>
    <li><strong>Complex conditional logic:</strong> "If this vehicle type, then calculate this way, unless this other condition, then..." Power BI's DAX can handle it, but it's not designed for application-level business logic.</li>
    <li><strong>Data entry and updates:</strong> The team wanted to input new fleet data directly in the tool. Power BI is for visualization and analysis, not data entry.</li>
    <li><strong>Custom export formats:</strong> Getting data out in exactly the format needed for other tools required workarounds.</li>
</ul>

<p style="font-size:0.8em">
Each limitation meant either finding a workaround (which sometimes made things more complex), or explaining why that feature wouldn't work well in Power BI. Some features we implemented anyway because they were critical, even if the implementation felt clunky. Others we had to push back on.
</p>

<p style="font-size:0.8em">
This created some frustration internally. The team could see what they wanted in their minds, and it was hard to explain why a tool that looked so flexible had these constraints.
</p>

<h2>Excel as the Data Layer</h2>
<p style="font-size:0.8em">
One decision that worked really well was keeping the data in Excel. This might sound like a step backward (why not use a proper database?), but it solved a critical problem.
</p>

<p style="font-size:0.8em">
The team working on fleet projects includes people with varying technical skills. Some are Excel experts, others are less technical. Everyone needed to be able to update the dataset when they completed a project, without depending on me or requiring special training.
</p>

<p style="font-size:0.8em">
Excel meant:
</p>
<ul style="font-size:0.8em">
    <li>Anyone on the team can open it and understand the structure</li>
    <li>Data entry doesn't require technical knowledge</li>
    <li>No database administration or special permissions needed</li>
    <li>Easy to back up, share, and version control (just save a new copy)</li>
    <li>Power BI connects to it seamlessly</li>
</ul>

<p style="font-size:0.8em">
I built VBA forms to make data entry more structured and reduce errors, but the underlying data is in familiar Excel tables. This accessibility has been crucial for keeping the database up to date.
</p>

<h2>The Evolution of Scope</h2>
<p style="font-size:0.8em">
Looking at the file versions in the project folder, you can see the journey:
</p>
<ul style="font-size:0.8em">
    <li>August 2024: Basic concept</li>
    <li>September 2024: First working version</li>
    <li>December 2024: Major structural changes</li>
    <li>January 2025: Feature additions</li>
    <li>March 2025: Refinements and current version</li>
</ul>

<p style="font-size:0.8em">
The scope changed significantly between the first version and what exists now. We started thinking it would be a simple comparison tool. It became a comprehensive analysis platform with TCO calculations, consumption estimation, emissions analysis, and transition planning exports.
</p>

<p style="font-size:0.8em">
Some of that growth was good. Real-world use showed what features would actually add value. But some of it came from scope creep and unclear requirements at the start. If I could do it again, I'd spend more time upfront defining what version 1.0 should include and what could wait for later iterations.
</p>

<h2>What I Learned About Alignment</h2>
<p style="font-size:0.8em">
The biggest lessons from this project weren't technical. They were about communication and managing expectations.
</p>

<p style="font-size:0.8em">
<strong>What went wrong:</strong>
</p>
<ul style="font-size:0.8em">
    <li>I didn't clearly communicate Power BI's limitations early enough</li>
    <li>We didn't have concrete mockups of what the tool would look like before I started building</li>
    <li>Feature requests kept coming during development without re-evaluating priorities</li>
    <li>I said "yes" to too many things trying to deliver everything the team wanted</li>
</ul>

<p style="font-size:0.8em">
This created internal frustration. The team was disappointed when certain features weren't possible or didn't work as smoothly as expected. I felt caught between technical constraints and user needs.
</p>

<p style="font-size:0.8em">
<strong>What I learned:</strong>
</p>
<ul style="font-size:0.8em">
    <li><strong>Show, don't tell:</strong> Sketches and mockups communicate better than descriptions. Next time, I'd create visual mockups before any development.</li>
    <li><strong>Define constraints upfront:</strong> "Here's what this platform can and can't do" should be the first conversation, not a surprise later.</li>
    <li><strong>Set clear milestones:</strong> Version 1.0 delivers X. Version 2.0 adds Y. Don't try to build everything at once.</li>
    <li><strong>Push back constructively:</strong> "We can do that, but it'll add two weeks and might make other features more complex. Still worth it?" is better than just saying yes.</li>
    <li><strong>Document decisions:</strong> Write down what was agreed and why. Memory is unreliable when projects stretch over months.</li>
</ul>

<h2>Applying Lessons to the Truck Rating API</h2>
<p style="font-size:0.8em">
The experience with this project directly shaped how I approached the Truck Rating API later. That project went much more smoothly because I applied what I learned here.
</p>

<p style="font-size:0.8em">
For the API project:
</p>
<ul style="font-size:0.8em">
    <li>I created detailed structure diagrams before writing code</li>
    <li>We aligned on what the API would and wouldn't do in the first meeting</li>
    <li>I showed examples of similar APIs so expectations were realistic</li>
    <li>The scope was clearly defined with specific features for version 1.0</li>
    <li>We documented the architecture and design decisions as we went</li>
</ul>

<p style="font-size:0.8em">
The result was a smoother development process, fewer surprises, and a final product that matched what everyone expected. The lessons learned from the Fleet TCO Tool's challenges made the API project successful.
</p>

<h2>Technical Details</h2>
<p style="font-size:0.8em">
Despite the challenges, the technical implementation has some interesting aspects:
</p>

<h3 style="font-size:0.9em">Database Structure</h3>
<p style="font-size:0.8em">
The Excel database uses a relational structure:
</p>
<ul style="font-size:0.8em">
    <li>Vehicle specifications table (fact table)</li>
    <li>Project details table (context)</li>
    <li>Consumption data table (time series)</li>
    <li>Cost breakdown tables (TCO components)</li>
    <li>Lookup tables (vehicle types, fuel types, operational categories)</li>
</ul>

<p style="font-size:0.8em">
These tables connect through relationships designed in Miro and implemented in Power BI's data model.
</p>

<h3 style="font-size:0.9em">Power BI Implementation</h3>
<ul style="font-size:0.8em">
    <li><strong>Custom navigation:</strong> Bookmarks and button actions create the menu system</li>
    <li><strong>DAX measures:</strong> Complex calculations for TCO, emissions, consumption estimates</li>
    <li><strong>Parameters:</strong> Limited use of parameters for scenarios (learned to keep this simple)</li>
    <li><strong>Conditional formatting:</strong> Visual feedback based on calculation results</li>
    <li><strong>Export functionality:</strong> DAX Studio and custom scripts for data extraction</li>
</ul>

<h3 style="font-size:0.9em">VBA Forms</h3>
<p style="font-size:0.8em">
The Excel side includes VBA-based data entry forms with:
</p>
<ul style="font-size:0.8em">
    <li>Input validation</li>
    <li>Dropdown lists from lookup tables</li>
    <li>Automatic calculation of derived fields</li>
    <li>Data quality checks</li>
</ul>

<h2>What Actually Works Well</h2>
<p style="font-size:0.8em">
Despite the challenges and constraints, the tool does work and provides real value:
</p>
<ul style="font-size:0.8em">
    <li>The custom navigation makes it accessible to non-Power BI users</li>
    <li>TCO calculations based on historical data improve accuracy of estimates</li>
    <li>The Excel database is maintainable by the whole team</li>
    <li>The Miro design documentation makes updates easier</li>
    <li>Export functionality supports transition planning work</li>
    <li>The tool grows more valuable as the database expands</li>
</ul>

<p style="font-size:0.8em">
It's in active use across Mov3ment's projects, and the team has adapted to both its capabilities and limitations.
</p>

<h2>What I'd Do Differently</h2>
<p style="font-size:0.8em">
If I started this project over:
</p>
<ul style="font-size:0.8em">
    <li><strong>Week 1:</strong> Create detailed mockups and database diagrams. Get agreement before coding anything.</li>
    <li><strong>Week 2:</strong> Share a document listing platform capabilities and constraints. Make sure everyone understands what's possible.</li>
    <li><strong>Week 3:</strong> Define version 1.0 scope precisely. Create a "later versions" list for everything else.</li>
    <li><strong>During development:</strong> Weekly check-ins with work-in-progress demos. Surface issues early.</li>
    <li><strong>After each iteration:</strong> Document what changed and why. Keep a decision log.</li>
</ul>

<p style="font-size:0.8em">
These aren't revolutionary ideas, but I learned them the hard way on this project.
</p>

<h2>The Value of Constraints</h2>
<p style="font-size:0.8em">
Here's something I didn't expect: some of the platform limitations actually made the tool better.
</p>

<p style="font-size:0.8em">
Because Power BI isn't infinitely flexible, I had to make deliberate choices about what features were truly important. If I'd built this as a custom application with no constraints, it probably would have become bloated with half-used features.
</p>

<p style="font-size:0.8em">
The constraints forced simplicity. The tool does specific things well rather than trying to do everything poorly. That's actually a feature, not a bug.
</p>

<h2>Practical Applications</h2>
<p style="font-size:0.8em">
If you're building internal tools, especially in platforms like Power BI:
</p>
<ul style="font-size:0.8em">
    <li><strong>Understand platform limits early:</strong> Know what your tool can and can't do before promising features</li>
    <li><strong>Design before building:</strong> Use diagramming tools (Miro, Figma, even PowerPoint) to map structure and flow</li>
    <li><strong>Create mockups:</strong> Show what it will look like before it exists</li>
    <li><strong>Define version 1.0:</strong> Be very clear about what's in scope now versus later</li>
    <li><strong>Align expectations constantly:</strong> Don't assume everyone understands constraints or progress</li>
    <li><strong>Document decisions:</strong> Future you will thank present you</li>
    <li><strong>Learn from each project:</strong> Apply lessons to the next one (like I did with the API)</li>
</ul>

<p style="font-size:0.8em">
The technical skills matter, but project management and communication might matter more for successful delivery.
</p>

<h2>Current Status</h2>
<p style="font-size:0.8em">
The tool is actively used and continues to evolve. The database grows with each project, making future analyses more accurate. The team has adapted to what works well and found workarounds for limitations.
</p>

<p style="font-size:0.8em">
More importantly, I learned lessons about building tools, managing expectations, and working within constraints that have already made my next projects better. That might be the most valuable output from this entire experience.
</p>
