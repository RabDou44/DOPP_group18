# Data-Oriented Programming Paradigms – Group 18 – Train vs plane travel times

## To do:
### 1. Travel times only for trips that have direct train and plane connections
 - We need to match airports to train stations when they are in the same city – what counts as the same city? For example Brussels Charleroi is not so close to Brussels
 - We need to choose which trips to include in 'Europe'
 - Include info about average speed and max speed of trains
### 2. Travel times for indirect connections
 - This requires either timetable datasets or an API to know how long the connections are
 - Include info about the proportion of the trip spent waiting during a connection
### 3. Including the time to get to the airport / train station
 - This is more complicated and requires arbitrary definitions of what is counted as travel time



## Data
### Trains:
#### Datasets:
 - [Rail network (eurostat) ](https://ec.europa.eu/eurostat/databrowser/explore/all/transp?lang=en&subtheme=rail.rail_pa&display=list&sort=category&extractionId=rail_pa_nbpass)
 - [Railway travel times in England](https://www.gov.uk/government/statistical-data-sets/connectivity-travel-time-indicators-for-rail-stations-con02)
 - [Spain train travel times](https://data.renfe.com/dataset/horarios-de-alta-velocidad-larga-distancia-y-media-distancia/resource/25d6b043-9e47-4f99-bd91-edd51d782450)
 - [Rail transport performance in Europe 2021](https://cohesiondata.ec.europa.eu/dataset/Rail-transport-performance-in-Europe-2021/bp5k-ynxy/data_preview)
#### Web apps:
- [Chonotrains](https://www.chronotrains.com/fr/station/2988507-Paris/8)

### Planes:
#### Datasets:
- [SkyTeam global flights timetable ](https://services.skyteam.com/Timetable/Skyteam_Timetable.pdf?_ga=2.25666683.710666209.1702055361-974558943.1702055361)
- [Air transport measurements (eurostat)](https://ec.europa.eu/eurostat/databrowser/explore/all/transp?lang=en&subtheme=rail.rail_pa&display=list&sort=category&extractionId=rail_pa_nbpass)
- [ICAO - Un Agency](https://www.icao.int/Aviation-API-Data-Service/Pages/default.aspx)
- [EU Control](https://www.eurocontrol.int/dashboard/rnd-data-archive)

### General data:
- [French Ministry of Transport](https://transport.data.gouv.fr/)
- [Promising report from the European Comission ](https://ec.europa.eu/regional_policy/sources/work/2023-rail-vs-air_en.pdf)
- [Data Travel Air Rail 2017-2018](https://figshare.com/articles/dataset/DATA_Travel_Time_Survey_AIR_RAIL_xlsx/6400832)

### Isochrones:
 - [Isochrones for Singapore: tutorial on Medium](https://medium.com/@zshaoz/reachable-sg-an-attempt-to-visualize-accessibility-in-singapore-using-isochrone-maps-ded88a334a9d)
 - [Mapbox Isochrone API on community.tableau.com](https://community.tableau.com/s/news/a0A8b00002GQgG4EAL/travel-time-isochrones-with-mapbox)
 - [Isochrones in Stockholm with Trafiklab API](https://rmattila.github.io/2021/01/15/isochrones/)

Questions:

 - How do rail travel times compare to air travel times between cities in Europe?
   
   Required data:
    - Cities (from/to)
    - Travel time
    - Distance (km)
    - Speed
    - Type of travel (rail/air)

 - Are there routes on which high-speed rail leads to shorter journey times than air travel?

   Due to limited number of high-speed rail routes in Europe (France, Belgium, Spain) there can be cosidered hypothethical routes between other european cities

   Required data:
    - Cities (from/to)
    - Travel time
    - Distance (km)
    - Speed
    - Type of travel (rail/air)

 - How can estimates of travel time to and from airports be included?
   
    The question is what to consider as a starting point for calculation of travel time: city centre, the main station, other stations? The easiest would be to calculate travel time to airport from city centre.
    Dataset avia_tf_arp_co shows if given airports have connections to other means of transports

 - Which is the most well-connected city in Europe in terms of minimising travel times to other cities? 

   Proposition:
   1) maesure cities in terms of they degree (number of degree connections to other cities)
   2) compute all cities closeness $C_{cl}(v)  = \sum_{u \in V} \frac{1}{d(u,v)}$
   for each $v \in V$ where (V - set of cities), where $d(u,v)$ is distance between cities.
   3) compute betweeness and compare 

 - Visualisation of isochrones would be useful in answering these questions. (how to build it?)

Idea: assigning weights to connections when making averages, so that small connections don’t disproportionately affect the average

Questions we want to discuss: 


What’s expected: 
1. the questions that you plan to answer, 
2. the datasets that you plan to use, 
3. how you plan to answer the questions, 
4. how the work will be divided up between the group members


