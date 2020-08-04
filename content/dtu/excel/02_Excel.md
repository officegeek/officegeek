---
title: "Excel dag 2"
date: 2018-12-29T11:02:05+06:00
weight: 3
draft: false
---

## Opslagsfunktioner
Excel har flere funktioner som du kan bruge til at finde værdier i et datasæt. De mest brugte er:

- **LOPSLAG** - Søger i øverste række af en matrix og flytter på tværs af rækken for at returnere en celleværdi
- **VOPSLAG** - Søger i den øverste række af en matrix og returnerer værdien af den angivne celle
- **INDEKS** - Anvender et indeks til at vælge en værdi fra en reference eller en matrix
- **SAMMENLIGN** - Slår værdier op i en reference eller en matrix


### LOPSLAG
Brug **LOPSLAG** når du vil finde data i en tabel eller et område efter række værdier.

Hvis det er syntaksen for LOPSLAG er:

**VLOOKUP(lookup_value,table_array,col_index_num,[range_lookup])**

[LOPSLAG](https://support.office.com/da-dk/article/lopslag-funktionen-0bbc8083-26fe-4963-8ab8-93a18ad188a1?wt.mc_id=otc_tips)

Microsoft har oprettet en pdf der giver en oversigt over **LOPSLAG**
[LOPSLAG Reference PDF](https://download.microsoft.com/download/9/b/4/9b49c8c5-d7a9-45b1-b8b6-52067e9970a8/AF101984660_en-us_xl_qrc_vlookup%20refresher.pdf)

Microsoft har også oprettet en fejlfindings oversift

[Fejlfindings PDF LOPSLAG](https://download.microsoft.com/download/3/4/0/340f95a5-33cd-45a5-8701-7efa0cf82daf/AF102038056_en-us_xl_qrc_vlookup_troubleshooter.pdf)

Video omkring [Lookup Functions in Excel](https://vimeo.com/87812779)

## Tabeller
Hvis du arbejder med data i Excel, og det kommer du til, så er tabeller et rigtigt stærkt og meget anvendiligt værktøj.

Microsoft vejledninger:

[Microsoft kursus tabeller](https://support.office.com/da-dk/article/video-opret-en-tabel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f?ui=da-DK&rs=da-DK&ad=DK)
[Oversigt over Excel-tabeller](https://support.office.com/da-dk/article/oversigt-over-excel-tabeller-7ab0bb7d-3a9e-4b56-a3c9-6c94334e492c)
[Oprette relationer mellem tabeller i Excel](https://support.office.com/da-dk/article/oprette-relationer-mellem-tabeller-i-excel-fe1b6be7-1d85-4add-a629-8a3848820be3)
[Kompatibilitetsproblemer med Excel-tabeller](https://support.office.com/da-dk/article/kompatibilitetsproblemer-med-excel-tabeller-1e9c9c83-bf17-41c7-b243-c48625a7a6ff)

## PivotTabel
En **PivotTabel** er et effektivt værktøj til at beregne, opsummere og analysere data, der gør det muligt at se sammenligninger, mønstre og tendenser i dataene.

[PivotTabel](https://support.office.com/da-dk/article/oprette-en-pivottabel-for-at-analysere-regnearksdata-a9a84538-bfe9-40a9-a8e9-f99134456576?ui=da-DK&rs=da-DK&ad=DK)

### PivotTabel Feltlisten
Når du har oprettet en pivottabel, får du vist feltlisten. Du kan ændre pivottabellens design ved at tilføje og arrangere dens felter. Hvis du vil sortere eller filtrere de kolonner med data, som vises i pivottabel, skal du se Sortere data i en pivottabel og Filtrere data i en pivottabel.

[Feltlisten](https://support.office.com/da-dk/article/brug-af-feltlisten-til-at-arrangere-felter-i-en-pivottabel-43980e05-a585-4fcd-bd91-80160adfebec)

### Gruppér data
Når du grupperer data i en pivottabel, kan det vise dig et undersæt af data, der skal analyseres.

[Gruppér eller opdel en gruppe af data i en pivottabel](https://support.office.com/da-dk/article/grupp%C3%A9r-eller-opdel-en-gruppe-af-data-i-en-pivottabel-c9d1ddd0-6580-47d1-82bc-c84a5a340725?ui=da-DK&rs=da-DK&ad=DK)

### Beregn værdier i en PivotTabel
I en pivottabel kan du bruge summeringsfunktioner i værdifelter til at kombinere værdier fra den underliggende datakilde. Hvis summeringsfunktioner og brugerdefinerede beregninger ikke giver de resultater, du ønsker, kan du oprette dine egne formler i beregnede felter eller beregnede elementer. Du kan f.eks. tilføje et beregnet element med formlen for salgsprovisioner, som kunne være forskellige fra område til område. Pivottabellen medtager derefter provisionen i subtotaler og hovedtotaler.

[Beregn værdier i en pivottabel](https://support.office.com/da-dk/article/beregn-v%C3%A6rdier-i-en-pivottabel-11f41417-da80-435c-a5c6-b0185e59da77)

### PivotDiagram
Nogle gange er det svært at se det store billede, når dine ubehandlede data ikke er blevet opsummeret. Din første Instinct kan være at oprette en pivottabel, men ikke alle kan se tal i en tabel og hurtigt se, hvad der foregår. Pivotdiagrammer er en god måde at føje datavisualiseringer til dine data.

[PivotDiagram](https://support.office.com/da-dk/article/opret-et-pivotdiagram-c1b1e057-6990-4c38-b52b-8255538e7b1c)

### Slette en PivotTabel
Når du ikke længere har brug for en pivottabel, skal du markere hele pivottabellen og trykke på Delete for at fjerne den.

[Slet PivotTabel](https://support.office.com/da-dk/article/slette-en-pivottabel-1de9b894-9178-43b3-b436-92e3ddb9175b)

## Udsnitsværktøjer
Udsnitsværktøjer giver dig knapper, som du kan klikke på for at filtrere **Tabeldata** eller **Pivottabeldata**. 
Ud over hurtig filtrering angiver udsnitsværktøjer også den aktuelle filtreringstilstand, hvilket gør det nemt at forstå, hvad der præcis vises i en filtreret pivottabel.

[Udsnitsværktøjer](https://support.office.com/da-dk/article/brug-udsnitsv%C3%A6rkt%C3%B8jer-til-at-filtrere-data-249f966b-a9d5-4b0f-b31a-12651785d29d)

## PivotTabel Tidslinje
I stedet for at justere filtre for at få vist datoer kan du bruge en tidslinje i en pivottabel – en dynamisk filtreringsindstilling, hvor du kan nemt kan filtrere efter dato/klokkeslæt og zoome ind på det ønskede tidsrum ved hjælp af et skyderkontrolelement. Klik på Analysér > Indsæt en Tidslinje for at indsætte en på regnearket.

[PivotTabel Tidslinje](https://support.office.com/da-dk/article/opret-en-pivottabel-tidslinje-til-at-filtrere-datoer-d3956083-01be-408c-906d-6fc99d9fadfa)