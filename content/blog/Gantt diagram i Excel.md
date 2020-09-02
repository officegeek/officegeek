---
title: "Gantt diagram i Excel"
icon: "ti-direction" # themify icon pack : https://themify.me/themify-icons
description: "Opret Gantt diagram i Excel"
# type dont remove or customize
type : "Excel"
draft: false
---

Gantt diagrammer er nyttige når du vil visualisere et projekts opgaver på en tidslinje. Microsoft Project er et super program til at oprette Gantt diagrammer, men det kan godt være lidt omfattende i forhold til de felestes behovet.

Her er mit bud på hvordan du kan oprette et interaktivt Gantt diagram i Excel.


## Data
Jeg har 6 koloner med data:

1. Faser
2. Aktivitet
3. Ansvarlig
4. StartDato
5. Antal Arbejdsdage
6. SlutDato

Du kan fjerne eller tilføje ekstra kolonner, så det passer til dit behov.  
Data er i en tabel, som har navnet: *Data*  
tabellen er placert i et selvstændigt ark - *Data*.

![Gantt_Tabel](/images/Gantt_Tabel.jpg)


## Pivot tabel
På basis af tabellen skal der oprettes en Pivot tabel, som danner grundlag for Gantt diagrammet.

![Gantt_Pivot_Tabel](/images/Gantt_Pivot_Tabel.jpg)

De felter der er med i Pivot tabellen er:

* Aktivitet
* StartDato
* SlutDato

*StartDato* og *SlutDato* skal have ændret beregning til henholdsvis *Min* og *Maks*.

Placer Pivot tabellen i et selvstændigt ark - her *PivotData*

## Gant diagram
Selev Gantt diagrammet består af to dele:

1. Tekst med oplysninger om de enkelte opgaver
2. Selve diagrammet

![Gantt_Pivot_Diagram](/images/Gantt_Diagram.jpg)

Jeg har desuden tilføjet to *Udsnit* værktøjer der gør det nemt at vælge *Facer* og *Ansvarlig*.  
Gant diagrammet er placert i et selvstændigt ark: *Gantt*.

De 4 overskrifter er indtastet:

* Aktivitet
* Start dato
* Slut dato
* Varighed

#### Varighed
Er beregnet med følgende formel:

*=HVIS.FEJL(ANTAL.ARBEJDSDAGE(C10;D10);"")*

Den giver antallet af arbejdsdage mellem *StartDato* og *SlutDato*

Der er brugt *Betingetformatering* til at vise søjlerne i celler.  
Den er oprettet med en *Formattypografi* som hedder *Datasøjle* og formatet er baseret på værdien i cellerne. Du kan selv vælge den farve som passer dig.

![Gantt_Søjler_Varighed](/images/Gantt_Formatering1.jpg)

#### Værdier
Værdierne i; *Aktivitet*, *StartDato* og *Slut Dato* kommer fra Pivot tabellen, *Data*, i arket *PivotData*.

Det er denne formel der er brugt:  

*=HVIS(PivotData!B3="";"";PivotData!B3)*

Årsagen til at der er brugt en *HVIS* funktion er at så du nemt kan udvide dine data uden at skulle ændre/tilføje ekstra formler.

### Gantt diagrammet
Selve Gant diagrammet består af flere elementer:

* Dato linjen
* Søjler for *Aktiviteterne*
* Markering af *DagsDato*

#### Dato linjen
Dato linjen brugere også Pivot tabellen, *Data*, fra arket *PivotData*.

Datoer er placeret i række *9*. Der er brugt Betinget formatering til at vise lørdage og søndage med rød tekst.

Den første/"mindste" startdato er placeret i cellen *F9* og den bliver hentet med denne formel:

*=MIN(Data[StartDato])*

De efterfølgende datoer i, *G7*, *H7*, *I7* osv. findes med formlen: *=F9+1*

Række *8* ugedagen er hentet fra række *9*. For derefter at bliver formateret til at kun at vise ugedagen - *ddd*.

![Gantt_Dato](/images/Gantt_Dato.jpg)


#### Dagsdato
For at gøre det nemmere at overskue Gantt diagrammet er der en markering af dags dato. Denne markering er oprettet ved hjælp af *Betinget formatering*.

![Gantt_Dato](/images/Gantt_DagsDato.jpg)

Den betingede formatering er oprette ved hjælp af en formel:

*=OG($B10<>"";F$7=IDAG())*

Formlene checker om cellen i *Aktivites* kolonnen er tom og om dato værdien i række *9* er ligmed *DagsDato*.

Dagsdato finder du ved at bruge formlen: *IDAG()*  
Du vælger den farve der passer til dit layout.

![Gantt_Dato](/images/Gantt_DagsDato_2.jpg)


#### Søjler for *Aktiviteter*
Gantt søjlerne vises også ved brug af betinget formatering. Jeg brugere en formel til at finde to betingelser:

1. Cellen i *StartDato* er ikke tom
2. Datoerne i *Dato rækken - 9* er ligmed eller ligger imellem *StartDato* og *SlutDato* for den givne Aktivitet.

Det har jeg gjort ved at bruge denne formel:

*=OG($C10<>"";MEDIAN($C10;$D10;F$9)=F$9)*

Det er et eksempel på hvordan du kan bruge *MEDIAN* til at undersøge om en værdi er mellem to grænseværdier.

#### Striber
For at gøre Gantt diagrammet mere læsbart er hveranden række farvet *grå*. Dette er gjort ved hjælp af betinget formatering.

![Gantt_Dato](/images/Gantt_Striber.jpg)

Formlen der er brugt er denne:

*=OG($B10<>"";REST(RÆKKE();2)=0)*

#### Betinget formatering
Der er tre *formler* for betinget formatering.

![Gantt_Dato](/images/Gantt_Betingetformatering.jpg)

Rækkefølgenden på de tre formateringer er sat så *søjlerne* altid er *først* så kommer *Dagsdato* og til sidst de grå linjer.

### Udsnitsværktøj
For at gøre udvælgelsen af: *Faser* og *Ansvarlig* er der oprettet to udsnitsværktøjer.

![Gantt_Dato](/images/Gantt_Udsnits.jpg)

De er oprettet på basis af Pivot tabellen, *Data*, i arket *PivotData*.


## Opdatering
Opdateringer, ændringer, skal du fortage i arket *Data*.

Når du har ændret, tilføjet eller fjernet noget skal arket opdateres. 

Det kan du gøre på to måder:

* Genvejstast - *Alt + CTRL + F5*
* Menu - *Data - Opdater alle*

