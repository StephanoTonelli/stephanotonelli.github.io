---
title: "Excel Tool for Reversing Wing Section Dots"
layout: single
author_profile: false
image: \assets\icon-microsoft-excel.png
categories:
  - Engineer
tags:
  - Excel
---

<p style="font-size:0.8em">
    In the process of designing a new remote-controlled airplane, I encountered the challenge of reversing the wing section dots to align the axis at the bottom of the design. This was necessary to replicate the design on CAD software, perform airflow simulations, or create blueprints for construction. To streamline this critical task, I developed a user-friendly Excel tool that automates the dot reversal process from Y- to Y+. This Excel tool effectively transformed the wing section coordinates, saving time and ensuring accurate representations for further analysis and manufacturing.
  </p>
  <h3>Key Features:</h3>
  <ul style="font-size:0.8em">
    <li>Automated Dot Reversal: The Excel tool automatically reversed the Y- coordinates to Y+ for wing section dots, ensuring the correct orientation for CAD software and other applications.</li>
    <li>User-Friendly Interface: The tool featured a simple and intuitive interface, enabling users to input the wing section data easily and obtain the reversed coordinates effortlessly.</li>
    <li>Precise Replication: By accurately aligning the wing section axis at the bottom, the tool ensured precise replication for airflow simulations, blueprint creation, and other design-related activities.</li>
    <li>Time and Resource Savings: The Excel tool significantly reduced manual labor and potential errors, saving valuable time and resources in the design and analysis process.</li>
  </ul>
  <h3>Technologies Used:</h3>
  <ul style="font-size:0.8em">
    <li>Microsoft Excel: I utilized Microsoft Excel's powerful data manipulation and calculation capabilities to develop the user-friendly tool.</li>
  </ul>
  <p style="font-size:0.8em">
    The Excel Tool for Reversing Wing Section Dots demonstrated my commitment to streamlining engineering processes through innovative and practical solutions. By automating the dot reversal task, I facilitated the design workflow for remote-controlled airplane wing sections, enabling more efficient analysis and construction. This project exemplified my proficiency in leveraging technology to overcome challenges and enhance productivity in the field of engineering design.
  </p>

  <a href="\assets\wings-1.xlsm" download>Download the file</a>
<p></p>
  <code>

  Sub Transformar()
'
' Macro3 Macro
'

Application.ScreenUpdating = False
Sheets("Planilha de apoio").Visible = True
    Range("D1").Select
    Selection.End(xlDown).Select
    Selection.End(xlDown).Select
    Range(Selection, Selection.End(xlDown)).Select
    Range(Selection, Selection.End(xlToRight)).Select
    Selection.Copy
    Sheets("Planilha de apoio").Select
    Range("B2").Select
    ActiveSheet.Paste
    Application.CutCopyMode = False
    ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort.SortFields.Clear
    ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort.SortFields.Add Key:=Range( _
        "A1"), SortOn:=xlSortOnValues, Order:=xlDescending, DataOption:= _
        xlSortNormal
    With ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort
        .Header = xlYes
        .MatchCase = False
        .Orientation = xlTopToBottom
        .SortMethod = xlPinYin
        .Apply
    End With
    Range("B2").Select
    Selection.End(xlDown).Select
    Range(Selection, Selection.End(xlToRight)).Select
    Range(Selection, Selection.End(xlDown)).Select
    Selection.Cut
    Sheets("1").Select
    Application.Goto Reference:="R1C4"
    Selection.End(xlDown).Select
    Selection.End(xlDown).Select
    ActiveSheet.Paste
    Sheets("Planilha de apoio").Select
    Application.Goto Reference:="R1C1"
    ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort.SortFields.Clear
    ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort.SortFields.Add Key:=Range( _
        "A1"), SortOn:=xlSortOnValues, Order:=xlAscending, DataOption:= _
        xlSortNormal
    With ActiveWorkbook.Worksheets("Planilha de apoio").AutoFilter.Sort
        .Header = xlYes
        .MatchCase = False
        .Orientation = xlTopToBottom
        .SortMethod = xlPinYin
        .Apply
    End With
    Sheets("1").Select
    Application.Goto Reference:="R1C1"
Sheets("Planilha de apoio").Visible = False
    Application.ScreenUpdating = True
End Sub

  </code>