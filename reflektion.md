# Reflektion — Inlämning 1

**Namn:** Yuk Ting Ku

**Datum:** 2026-10-19

---

## Vad var svårast?

Det svåraste var att rita ER-diagrammet eftersom det var första gången jag gjorde ett sådant diagram. De andra delarna gick ganska bra för mig.

---

## Vad lärde du dig?

Jag lärde mig hur man skapar en databas från grunden och hur man använder primärnycklar och främmande nycklar för att koppla ihop olika tabeller.
---

## Hur använde du SQL i praktiken — vad kändes naturligt och vad var förvirrande?

Jag har tidigare arbetat på ett telekomföretag där jag använde SQL. Därför kändes det ganska naturligt att hämta data från en databas. Däremot har jag mest hämtat data och inte skapat en databas från grunden, så det var nytt för mig.
---

## Om du hade mer tid — vad hade du lagt till eller gjort annorlunda?

Jag skulle nog ha gjort på ungefär samma sätt, eftersom jag är ganska nöjd med resultatet. Jag skulle däremot lägga mer tid på att planera och rita ER-diagrammet från början.
---

## (VG) Varför valde du just den här tabellstrukturen?

Resonera kring ditt designval: Vad hade hänt om du löst det på ett annat sätt? Vilka för- och nackdelar ser du med din lösning jämfört med ett alternativ?

Jag valde att dela upp databasen i tre tabeller: artists, albums och songs. På dess sätt kan jag lagra information om artister, album och låtar separat och koppla ihop tabellerna med Primary key och foreign key som jag har lagt mig på nordmaliserings lektion.

Om jag hade lagt all information i en enda tabell skulle samma information, till exempel artistens namn och albumets årtal, behöva upprepas flera gånger. Det skulle kunna göra databasen svårare att uppdatera och öka risken för fel.

En fördel med min lösning är att den minskar onödig duplicering av data och gör det enklare att hämta information från flera tabeller med JOIN. En nackdel är att vissa frågor blir lite mer komplicerade eftersom jag behöver koppla ihop tabellerna.
