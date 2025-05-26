# KI-dashboard
Magistritöö kood -  MSc thesis code
# Ravikvaliteedi Indikaatorite töölaud

See repo sisaldab Shiny-põhist rakendust, mis kuvab onkoloogilisi ravikvaliteedi indikaatoreid OHDSI CohortGenerator ja CirceR paketiga genereeritud kohortide pealt.

## Funktsioonid

- **Kohortide genereerimine**  
  Loeb JSON-failid, loob ja täidab PostgreSQL andmebaasis kohorditabelid  
- **Indikaatorite arvutamine**  
  Summeerib indikaatorite arvutamiseks vajalikud patsientide arvud kohortides ning arvutab protsentuaalsed osakaalud  
- **Interaktiivne dashboard**

  — Avaleht: patsientide arv, kohortide tabel, ülevaate graafik

  — Indikaatorite alamvaated: kuvatakse väärtused aastate, terviseteenuse osutajate või mõlema lõikes  
- **Modulaarne paigutus**  
  Eraldi lehed emakakaela-, eesnäärme-, rinna- ja kolorektaalvähiga seotud indikaatoritele

## Eeldused

- R 
- Juurdepääes PostgreSQL andmebaasile OHDSI Common Data Modeliga   
- Järgnevad R-paketid:

  ```r
  install.packages(c(
    "DatabaseConnector",
    "CohortGenerator",
    "CirceR",
    "dplyr",
    "stringr",
    "ggplot2",
    "plotly",
    "DT",
    "shinydashboard"
  ))

## Andmebaasiühendus
### Loo fail ~/.Renviron järgmiste ridadega
```
DB_HOST=server

DB_NAME=OMOP andmebaasi nimi

DB_USERNAME=kasutajanimi

DB_PASSWORD=parool
```

Veendu, et kaust /CohortJSONs/ sisaldab kõiki lugeja ja nimetaja .json faile.


## Rakenduse käivitamine
```
library(shiny)
runApp(dasboard_QI)
```
Esimene käivitamine genereerib kohortitabelid ja salvestab cohortData.rds.

Edaspidine käivitamine loeb andmed cohortData.rds failist ja on kiirem.

### Repo kloonimine

```bash
git clone https://github.com/sinu_kasutajanimi/ravikvaliteedi-dashboard.git
cd ravikvaliteedi-dashboard
```

Koodi kirjutamisel ja kohendamisel on kasutatud ka tehisintellektil põhineva OpenAI keelemudeli ChatGPT o3 abi.
