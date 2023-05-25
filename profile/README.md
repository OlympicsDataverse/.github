---
output: github_document
always_allow_html: yes
---

<!-- README.md is generated from README.Rmd. Please edit that file -->

```{r, include = FALSE}
library(tidyverse)
knitr::opts_chunk$set(
  collapse = TRUE,
  comment = "#>"
)
```

# About the OlympicsDataverse

<!-- badges: start -->

<!-- badges: end -->

Inspiration coming from the <https://github.com/sportsdataverse>, I found there was no common place with Olympic data. After discovering some sports have public access to data I decided to start this organization with the intent of a data distribution knowledge base.

### Sources:

-   <https://en.wikipedia.org/wiki/Olympic_sports>

-   <https://olympics.com/en/sports/>

```{r}
#| echo: false
library(knitr)
summer <- dplyr::tibble(
  Sport = c('Artistic Swimming', "Diving", "Marathon Swimming", "Swimming", "Water Polo", "3x3 Basketball", "Basketball", "Canoe Sprint", "Canoe Slalom", "Cycling BMX Freestyle", "Cycling BMX Racing", "Cycling Mountain Bike", "Cycling Road", "Cycling Track", "Artistic Gymnastics", "Rhythmic Gymnastics", "Trampoline Gymnastics", "Volleyball - Beach", "Volleyball - Indoor", "Equestrian - Dressage", "Equestrian - Eventing", "Equestrian - Jumping", "Wrestling - Freestyle", "Wrestling - Greco-Roman", "Archery", "Athletics", "Badminton", "Boxing", "Breaking", "Fencing", "Field hockey", "Football", "Golf", "Handball", "Judo", "Modern Pentathlon", "Rowing", "Rugby Sevens", "Sailing", "Shooting", "Skateboarding", "Sport Climbing", "Surfing", "Table Tennis", "Taekwondo", "Tennis", "Triathlon", "Trampoline", "Weightlifting"),
  `Sport (initial)` = c("SWA", "DIV", "OWS", "SWM", "WPO", "BK3", "BKB", "CSP", "CSL", "BMF", "BMX", "MTB", "CRD", "CTR", "GAR", "GRY", "GTR", "VBV", "VVO", "EDR", "EVE", "EJP", "WRE", "WGR", "ARC", "ATH", "BDM", "BOX", "BKG", "FEN", "HOC", "FBL", "GLF", "HBL", "JUD", "MPN", "ROW", "RU7", "SAL", "SHO", "SKB", "CLB", "SRF", "TTE", "TKW", "TEN", "TRI", "GTR", "WLF"),
  Body = c("WAqua", "WAqua", "WAqua", "WAqua", "WAqua", "FIBA", "FIBA", "ICF", "ICF", "UCI", "UCI", "UCI", "UCI", "UCI", "FIG", "FIG", "FIG", "FIVB", "FIVB", "FEI", "FEI", "FEI", "UWW", "UWW", "WArch", "WAthle", "BWF", "AIBA", "WDSF", "FIE", "FIH", "FIFA", "IGF", "IHF", "IJF", "UIPM", "WRow", "WRug", "WSail", "ISSF", "WSkate", "IFSC", "ISA", "ITTF", "WT", "ITF", "ITU", "FIG", "IWF"),
  `Sporting Body Webpage` = c("www.worldaquatics.com", "www.worldaquatics.com", "www.worldaquatics.com", "www.worldaquatics.com", "www.worldaquatics.com", "www.fiba.basketball", "www.fiba.basketball", "www.canoeicf.com", "www.canoeicf.com", "www.uci.org", "www.uci.org", "www.uci.org", "www.uci.org", "www.uci.org", "www.gymnastics.sport", "www.gymnastics.sport", "www.gymnastics.sport", "www.fivb.com", "www.fivb.com", "www.fei.org", "www.fei.org", "www.fei.org", "uww.org", "uww.org", "www.worldarchery.sport", "worldathletics.org", "http://bwfbadminton.com", "www.iba.sport", "www.worlddancesport.org", "http://fie.org", "www.fih.hockey", "www.fifa.com", "www.igfgolf.org", "http://www.ihf.info", "www.ijf.org", "www.uipmworld.org", "worldrowing.com", "www.world.rugby", 'www.sailing.org/', 'http://www.issf-sports.org/', 'http://www.worldskate.org/', 'http://www.ifsc-climbing.org/', 'www.isasurf.org/', 'www.ittf.com/', 'http://www.worldtaekwondo.org/', 'www.itftennis.com/en/', 'www.triathlon.org/', "www.gymnastics.sport/site/", 'iwf.sport/'),
  `Packages or API` = c(
    'api.worldaquatics.com/fina/competitions/3085/events', 'api.worldaquatics.com/fina/competitions/3085/events', 'api.worldaquatics.com/fina/competitions/3085/events', 'api.worldaquatics.com/fina/competitions/3085/events', 'api.worldaquatics.com/fina/competitions/3085/events', "cm.fibaorganizer.com/static/docs/api/", "cm.fibaorganizer.com/static/docs/api/", "infoicf.msl.es/webICF/searcherOneSport?page=ZZS100R_@@@@@@@@@@@@@@@@@@@@@ENG", "infoicf.msl.es/webICF/searcherOneSport?page=ZZS100R_@@@@@@@@@@@@@@@@@@@@@ENG", "www.uci.org/api/calendar/upcoming", "www.uci.org/api/calendar/upcoming", "www.uci.org/api/calendar/upcoming", "www.uci.org/api/calendar/upcoming", "www.uci.org/api/calendar/upcoming", "www.gymnastics.sport/api/", "www.gymnastics.sport/api/", "www.gymnastics.sport/api/", "www.fivb.org/VisSDK/VisWebService/#Introduction.html", "www.fivb.org/VisSDK/VisWebService/#Introduction.html", "inside.fei.org/fei/your-role/it-services/it-platforms/fei-database", "inside.fei.org/fei/your-role/it-services/it-platforms/fei-database", "inside.fei.org/fei/your-role/it-services/it-platforms/fei-database", "github.com/unitedworldwrestling", "github.com/unitedworldwrestling", "www.worldarchery.sport/api", "None found", "extranet-lv.bwfbadminton.com/api", "None found", "services.worlddancesport.org/api/1", "None found", "None found", "futdb.app", "None found", "None found", "judobase.ijf.org/", "None found", "None found", "github.com/pierre-lamarche/RugbyRanking", "None found", "None found", "None found", "None found", "None found", "None found", "None found", "None found", "github.com/tyler-widdison/rTriathlon", 'None found', "None found")
  )

kableExtra::kbl(summer) %>% 
    kableExtra::kable_paper() %>% 
    kableExtra::scroll_box(height = "400px")


```
