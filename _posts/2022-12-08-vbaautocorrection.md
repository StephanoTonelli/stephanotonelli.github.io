---
title: "VBA Code for Autocorrecting Tests on Excel"
layout: single
author_profile: false
image: \assets\icon-microsoft-excel.png
categories:
  - Programming
  - Business
tags:
  - VBA
---

<p style="font-size:0.8em">
I made this VBA project on my internship in a SupplyChain Consultancy it aims to streamline the process of correcting the test on Microsoft Excel we used to apply on possible new employes. By running through the folder and opening the test files of each candidate the code reads the answers provided by the candidate and compares them to the correct answers on the correction file, filling the score of each candidate along with their names. The cell formatting scores must be inputed manually to calculate the full score.
</p>
<p style="font-size:0.8em">
Benefits:
</p>


<ul style="font-size:0.8em">
  <li>Saves time and effort in correcting tests manually</li>
  <li>Ensures accuracy in scoring</li>
  <li>Can be easily customized to fit the needs of different tests and grading systems</li>
</ul>

<p style="font-size:0.8em">
Implementation:
</p>
<p style="font-size:0.8em">
The code is written in VBA and can be accessed and edited through the Visual Basic Editor in Microsoft Excel
The correct answers to the test must be entered into a separate sheet in the Excel file with the correction code.
The correction file must be on the same folder as all tests.
The code is triggered by a button click or can be set to run automatically when the workbook is opened.
</p><br>

<p style="font-size:0.8em">Folder with the files</p>
![Folder with the files](\assets\vbaautocorrection-0.png)

<p style="font-size:0.8em">Workbook with the scores and buttons</p>
![Workbook with the scores and buttons](\assets\vbaautocorrection-1.png)

<p style="font-size:0.8em">Sheet with the correct answers</p>
![Sheet with the correct answers](\assets\vbaautocorrection-2.png)

<p style="font-size:0.8em">The method of correction and values od each question</p>
![The method of correction and values od each question](\assets\vbaautocorrection-3.png)

<p style="font-size:0.8em">First Phase of the test</p>
![First Phase of the test](\assets\vbaautocorrection-4.png)

<p style="font-size:0.8em">Code:</p>

<pre><code style="font-size:0.7em;color: black">
Sub Correct()

'Stop refreshing screen
Application.ScreenUpdating = False

' unhide the template tab
Sheets("Template").Visible = True

'Define where the files are
Folder = Sheets(Sheet2.Index).Range("XFD2").Value
file = Dir(Folder & "*.xl*")

' Scan all files in the folder
Do Until file = ""
     'Verify that the next document to be opened is not the file 
     'that is running the macro (if it is, skip it)
     If file = ThisWorkbook.Name Then
     file = Dir() 'Dir() skip to the next file in the directory
     End If
    
     'Open document
     Workbooks.Open (Folder & File)
     Windows(file).Activate
     'take the name of the document and paste 
     'it in the file "correction" in worksheet 2
     name = file
     Windows("Correct.xlsm").Activate
     Sheets(Sheet2.Index).Select
     'variable to always paste the file name on the line below
     N = 2
     'select the line range depending on N
     Range(Range("A:A").Find(Empty).Address) = name
    
''''''''''''''''''''''''''''Copy PHASE 1 EX1
'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 1").Select

         'Select range to copy
         Range("C7:C16").Select
         Selection.Copy
        
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A1").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
        
''''''''''''''''''''''''''''Copy PHASE 1 EX2
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 1").Select
        

         'Select range to copy
         Range("C25:F33").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("C1").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
        
''''''''''''''''''''''''''''Copy PHASE 1 EX3
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 1").Select
        

         'Select range to copy
         Range("C37:D44").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("H1").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
        
''''''''''''''''''''''''''''Copy PHASE 1 EX4
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 1").Select
        

         'Select range to copy
         Range("C67:C77").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("K1").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
        
''''''''''''''''''''''''''''Copy PHASE 1 EX5
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 1").Select
        

         'Select range to copy
         Range("C81:F86").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("M1").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
        
''''''''''''''''''''''''''''Copy PHASE 2 EX2 and EX3
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 2").Select
        

         'Select range to copy
         Range("A26:L27").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A15").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
		 
		 ''''''''''''''''''''''''''''Copy PHASE 2 EX4
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 2").Select
        

         'Select range to copy
         Range("M11:M25").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("N15").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX1
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("G69").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A32").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX2
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("C14:C67").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("C32").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX3
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("G14:G67").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("E32").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX4
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("G72").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("G32").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX5
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("G74").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("I32").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 3 EX6
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 3").Select
        

         'Select range to copy
         Range("E76").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("K32").Select
         'Paste together with the formatting and formulas
         ActiveSheet.Paste
		 
''''''''''''''''''''''''''''Copy PHASE 4 EX1
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 4").Select
        

         'Select range to copy
         Range("K5:M93").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A88").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 5 EX1, EX2 and EX3
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 5").Select
        

         'Select range to copy
         Range("D28:K30").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A180").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 6 EX1
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 6").Select
        

         'Select range to copy
         Range("B26:M27").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A201").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 6 EX2
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 6").Select
        

         'Select range to copy
         Range("O11:O25").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("A185").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''Copy PHASE 6 EX3
     'Go back to the test window
     Windows(file).Activate
     'Select the first worksheet of the test
     Sheets("PHASE 6").Select
        

         'Select range to copy
         Range("P11:Y25").Select
         Selection.Copy
      
         ' open the correction file window
         Windows("Correct.xlsm").Activate
         'select the worksheet to paste
         Sheets(Sheet1.Index).Select
         ' Paste in this document in the cell indicated in the range
         Range("C185").Select
         ' Paste only the value
         Selection.PasteSpecial Paste:=xlPasteValues
        
''''''''''''''''''''''''''''
     'select the worksheet
     Sheets(Sheet1.Index).Select
     'Select range to copy
     Range("BL9").Select
     Selection.Copy
    
     'select the worksheet
     Sheets(Sheet2.Index).Select
     ' Paste in this document in the cell indicated in the range
     Range(Range("D:D").Find(Empty).Address).Select
     ' Paste only the value
     Selection.PasteSpecial Paste:=xlPasteValues
''''''''''''''''''''''''''''
''''''''''''''''''''''''''''
     ' Close the file without saving
     Workbooks(file).Close SaveChanges:=False
     'Select the next file in the folder
     file = Dir()
    
loop
' open the correction file window
Windows("Correct.xlsm").Activate
'arrange column C with the names
Worksheets(Sheet2.Index).Columns("C:C").AutoFit
Range("C1").Select
' hide the template tab
Sheets("Template").Visible = False
'Update screen
Application.ScreenUpdating = True

End Sub
</code></pre>

<pre><code style="font-size:0.7em;color: black">
SubClear()
'Do not refresh screen
Application.ScreenUpdating = False
     Range("H6,A2:A1048576,D2:D1048576,E2:E1048576,F2:F1048576").Select
     Range("F2").Activate
     Selection.ClearContents
     Range("C1").Select
'Update screen
Application.ScreenUpdating = True

End Sub
</code></pre>

<p style="font-size:0.8em">This VBA code project can be a useful tool for teachers, educators, HR or anyone who frequently needs to correct tests on Microsoft Excel. Try it out and see how it can streamline your test correction process!</p>