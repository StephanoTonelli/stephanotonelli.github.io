---
title: "Supply Chain Optimization with Google App Script"
layout: single
author_profile: false
image: \assets\icon-Google-Apps-Script.png
categories:
  - Programming
  - Business
  - Supply Chain
tags:
  - Google Apps Script

---

<div  style="font-size:0.8em"><p>In this project at a supply chain and fuel consultancy startup, our objective was to optimize trucking routes and costs by calculating the distance between different locations and feeding this data into a cost prediction tool. The entire project was built on Google Sheets using Google App Script.</p>

<h3><strong>Project Scope:</strong></h3>

<p></p>

<li  style="font-size:1em"><strong>Objective:</strong> To estimate the cost of truck trips between different locations and optimize transportation expenses for client companies.</li>

<li  style="font-size:1em"><strong>Tools Used:</strong> Google Sheets, Google App Script, and Excel.</li>

<li  style="font-size:1em"><strong>Startup Focus:</strong> Supply chain consultancy, fuel consultancy, and distribution.</li>

<h3><strong>Key Steps:</strong></h3>

<ol type="1" class="numbered-list" start="1"><li style="font-size:1em"><strong>Data Collection:</strong> We started by collecting a list of different places and their corresponding origins and destinations. This list was maintained in a Google Sheets document, with the first column representing the origin and the second column representing the destination.</li></ol>

<ol type="1" class="numbered-list" start="2"><li style="font-size:1em"><strong>Distance Calculation:</strong> Google App Script was employed to calculate the distance between each pair of locations. The script utilized the Google Maps API to accurately determine the distances.</li></ol>

<ol type="1" class="numbered-list" start="3"><li style="font-size:1em"><strong>Cost Prediction Tool:</strong> The distances obtained from the previous step were then populated in the third column of the Google Sheets document. This document with all three columns (origin, destination, and distance) served as the basis for the cost prediction tool.</li></ol>

<ol type="1" class="numbered-list" start="4"><li style="font-size:1em"><strong>Excel Integration:</strong> The final Google Sheets document was integrated with an Excel-based cost prediction tool. This Excel sheet took the list of origins, destinations, and distances as input and estimated the cost of truck trips based on predefined cost parameters.</li></ol>

<ol type="1" class="numbered-list" start="5"><li style="font-size:1em"><strong>Optimization Recommendations:</strong> Once the cost prediction tool was set up, we could analyze and compare different transportation routes, identify cost-saving opportunities, and provide optimization recommendations to our client companies.</li></ol>

<h3 class=""><strong>Image from Google Sheets:</strong></h3>

<p></p>

<img src="\assets\distancebetweencities-1.png" alt="Google sheets" style="float: left; margin-right: 20px;">

<p></p>

<h3 class=""><strong>Code from AppScript:</strong></h3>

<p></p>

<code style="font-size:0.8em">
// @ts-nocheck 

//Tool doesn't get the distance if there is any body of water on the way  

function dist() { 
  var planilha = "Ferramenta de Distâncias"; 
  var start = 1; 
  var end = 2; 
  var inicio = 2; 
  var colDist = 3; 
  var ss = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(planilha); 
  var lr = ss.getLastRow(); 

// Start from the first line without the distance filled 

while (ss.getRange(inicio,3).isBlank() == false){ 
  inicio += 1 
} 
  for (var i = inicio; i<= lr; i++) { 
    var endStart = ss.getRange(i,start).getValue(); 
    var endEnd = ss.getRange(i,end).getValue();

    /*Logger.log(endStart); 
    Logger.log(endEnd);*/ 

    var mapObj = Maps.newDirectionFinder(); 
    mapObj.setOrigin(endStart); 
    mapObj.setDestination(endEnd); 
    var directions = mapObj.getDirections(); 

    //To avoid errors due to islands, rivers or oceans, set -1 on errors

    //if (directions["routes"][0]["legs"] ) 

    try{ 
      var km = directions["routes"][0]["legs"][0]["distance"]["value"]/1000 
    }catch(erros){ 

      var km = -1 

    } 

    //Teste legs 

    //var kmm = directions["routes"][0]["legs"][0]["distance"]["value"]; 

    //Logger.log(kmm); 

    ss.getRange(i,colDist).setValue(km); 
   } 
}

</code>

<h3 class=""><strong>Benefits and Outcomes:</strong></h3>

<p></p>

<li  style="font-size:1em"><strong>Cost Savings:</strong> By accurately estimating the transportation costs and optimizing the routes, our startup's clients could significantly reduce their overall logistics expenses.</li>

<li  style="font-size:1em"><strong>Efficiency Improvement:</strong> The automation of distance calculations and cost predictions reduced manual work and improved the efficiency of the supply chain planning process.</li>

<li  style="font-size:1em"><strong>Competitive Advantage:</strong> Providing cost-effective and data-driven supply chain solutions helped our startup gain a competitive edge in the market.</li>

<li  style="font-size:1em"><strong>Long-Term Partnerships:</strong> Successful project implementation led to strengthened relationships with clients, who relied on our expertise for ongoing supply chain and fuel consultancy.</li>

<h3><strong>Conclusion:</strong></h3>

<p></p>

<p style="font-size:1em">By leveraging the power of Google Sheets, Google App Script, and Excel integration, our supply chain and fuel consultancy startup successfully developed a cost prediction tool that allowed clients to estimate and optimize trucking costs between different locations. This data-driven approach empowered companies to make informed decisions, reduce expenses, and improve overall supply chain efficiency, cementing our startup's position as a trusted partner in the supply chain and fuel consultancy domain.</p>