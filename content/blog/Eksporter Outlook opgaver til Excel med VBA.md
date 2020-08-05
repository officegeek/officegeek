
---
title: "VBA - Outlook opgaver til Excel"
icon: "ti-direction" # themify icon pack : https://themify.me/themify-icons
description: "Bruf VBA til at eksportere opgaver fra Outlook til Excel"
# type dont remove or customize
type : "VBA"
draft: false
---

En af de ting jeg syntes bedst om ved Microsoft Office pakken er det, at de enkelte programmer arbejder super godt sammen. Det er meget nemt gå fra det ene program til det andet, det er nemt at flytte data fra et program til et andet.

Jeg styrer mine opgaver i Outlook, men nogle gange er det en fordel at have dem i Excel. Det kan være fordi de skal bruges i en anden sammenhæng f.eks. i Word eller PowerPoint.
For nemt at eksportere opgaverne fra Outlook til Excel har jeg oprette en makro der gør det for mig.


### Outlook indstillinger
Når du arbejder med VBA i Outlook er det en fordel at have aktiveret fanen "Udvikler"

**Det gør du på denne måde:**

1. Klik på Filer - Indstillinger
2. Klik på "Tilpas båndet"
3. Sæt hak i "Udvikler"
4. Klik "Ok"

![Udvikler](/images/outlook_opgave_vba.jpg)

### Object Library
Når du fra et Microsoft Office program skal have adgang til et andet via VBA, skal du oprette en reference til dette programs Object Model.

1. Tools
2. References
3. Find og sæt hak i *Microsoft Excel 16.0 Object Libaray*  
Nummeret er afhængiet af din Office version

![Udvikler](/images/excel_object_library.jpg)
### Opret makroen
djksfhjksd

### VBA koden
```vbnet
Sub EksportOpgaverExcel()

' Variabler
    ' Find Dokumenet mappen - Variable
    Dim MyShell As Object
    Dim DocumentFolder As String
    
    ' Outlook - Variable
    Dim olnameSpace As Outlook.NameSpace
    Dim taskFolder As Outlook.MAPIFolder
    Dim tasks As Outlook.Items
    Dim task As Outlook.TaskItem
    
    ' Excel - Variable
    Dim appExcel As New Excel.Application
    Dim fileExcel As Excel.Workbook
    Dim fileNavn As String
    Dim FindesExcelFilen As Boolean
    
    ' Gennemløb variable
    Dim i As Integer
    Dim n As Integer
    n = 2 ' Start Row
    
    ' Find Dokument mappen
    Set MyShell = CreateObject("WScript.Shell")
    DocumentFolder = MyShell.SpecialFolders("MyDocuments")
    
    
    ' Opret Excel filen
    Set appExcel = CreateObject("Excel.Application")
    ' appExcel.Visible = True
    fileNavn = "MineOpgaver.xlsx"
    
    ' Findes filen?
    FindesExcelFilen = Dir(DocumentFolder & "\" & fileNavn) > ""
    
    If FindesExcelFilen Then
        ' Åben Excel filen
        Set fileExcel = appExcel.Workbooks.Open(DocumentFolder & "\MineOpgaver.xlsx")
    Else
        ' Opret Excel filen
        Set fileExcel = appExcel.Workbooks.Add
        fileExcel.SaveAs FileName:=DocumentFolder & "\" & fileNavn
    End If

    ' Outlook mapper
    Set olnameSpace = Application.GetNamespace("MAPI")
    Set taskFolder = olnameSpace.GetDefaultFolder(olFolderTasks)
    Set tasks = taskFolder.Items

    ' Opret overskrifter i Excel
    With fileExcel.Sheets(1)
        .Range("A1").Value = "Emne"
        .Range("B1").Value = "Forfaldsdato"
        .Range("C1").Value = "Pct. fuldført"
        .Range("D1").Value = "Status"
    End With
    
    ' Eksport af opgaver
    For i = 1 To tasks.Count ' Gennemløb af dine opgaver

        Set task = tasks.Item(i)

        If Not task.Complete Then
            With fileExcel.Sheets(1)
                .Range("A" & n).Value = task.Subject
                .Range("B" & n).Value = task.DueDate
                .Range("C" & n).Value = task.PercentComplete
                .Range("D" & n).Value = task.Status
            End With
            
            n = n + 1
        End If

    Next i
    
    ' Autofit kolonner
    fileExcel.Sheets(1).Columns("A:D").AutoFit
    
    ' Gem
    fileExcel.Save
    
    ' Oprydning
    fileExcel.Close
    Set fileExcel = Nothing
    appExcel.Quit
    
End Sub

```