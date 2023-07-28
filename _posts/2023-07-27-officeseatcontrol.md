---
title: "Office Seat Management Tool"
layout: single
author_profile: false
image: \assets\icon-microsoft-excel.png
categories:
  - Business
  - Supply Chain
tags:
  - Excel
---

  <p style="font-size:0.8em">
    As part of my work at a previous company, I developed a customized Excel-based Office Seat Management Tool to efficiently control seat occupancy and meeting room availability. The tool was hosted on the company's server and provided real-time updates on the seating status, allowing employees to know the availability of seats before arriving at the office. It streamlined the process of finding and reserving a spot, contributing to a more organized and productive work environment.
  </p>
  <img src="\assets\Office-Seat-1.png" alt="Office Seat Management Tool" class="image">
  <p></p>
  <a href="\assets\Office-Seat-0.xlsm" download>Download the File</a>
  <h3>Key Features:</h3>
  <ul style="font-size:0.8em">
    <li>Dynamic Seating Chart: The tool featured a user-friendly Excel interface with a dynamic seating chart, displaying the layout of the office and the availability of seats in real-time.</li>
    <li>Easy Reservation System: Employees could simply input their names and mark their chosen seats or meeting rooms in the Excel file to reserve the spot before coming to the office.</li>
    <li>Color-Coded Status: The tool used color-coded cells to indicate the availability status of each seat, making it easy for employees to identify available or occupied spots at a glance.</li>
    <li>Automated Updates: Any changes made by employees, such as seat reservations or cancellations, were automatically updated and reflected in the tool for everyone to see.</li>
    <li>Secure Server Hosting: The Excel file was securely hosted on the company's server, ensuring data privacy and accessibility only to authorized personnel.</li>
  </ul>
  <h3>Technologies Used:</h3>
  <ul style="font-size:0.8em">
    <li>Microsoft Excel: I utilized Microsoft Excel, a widely used spreadsheet software, to create the dynamic and interactive Office Seat Management Tool.</li>
    <li>Company Server: The tool was hosted on the company's server, allowing multiple employees to access and use it simultaneously from different locations.</li>
  </ul>
  <p style="font-size:0.8em">
    The Office Seat Management Tool significantly improved the office's daily operations by providing a clear overview of available seating options and meeting rooms. Employees could efficiently plan their workdays, saving time and effort while ensuring a seamless transition to a flexible work environment. This project demonstrated my ability to create practical solutions that integrate technology to optimize workplace productivity and efficiency.
  </p>

<code style="font-size:0.8em">
    Sub Novodia()
    Application.ScreenUpdating = False

      Union(Range("F3,F4,F5,F6,F8,F9,F10,F11,J3,J4,J5,J6,J8,J9,J10,J11,L3,L4,L5,L6,L8,L9,L10,L11") _
      , Range("P3,P4,P5,P6,P8,P9,P10,P11,R3,R4,R5,R6,R8,R9,R10,R11,V3,V4,V5,V6,V8,V9,V10,V11,L15,L16,L17,L18,Y15,Y16,Y17,Y18")).Select
        
        Range("F3:F11").ClearContents
        
        
        Selection.ClearContents
        
      Range("F23,L23,J23,P23,R23,V23").Select
        
        Selection.Value = ".........."
        
        Columns("F:F").EntireColumn.AutoFit
        Columns("L:L").EntireColumn.AutoFit
        Columns("J:J").EntireColumn.AutoFit
        Columns("P:P").EntireColumn.AutoFit
        Columns("R:R").EntireColumn.AutoFit
        Columns("V:V").EntireColumn.AutoFit
        
        Selection.ClearContents
        
            MsgBox "O dia mudou!", vbOKOnly, "Atualização"
        
        Dia = Range("C8").Value + 7
        
        Range("C8").Value = Dia

        Range("C8").Select
        
    Application.ScreenUpdating = True
    End Sub
</code>