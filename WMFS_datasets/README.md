# WMFS Datasets

Author: [Huanfa Chen](huanfa.chen@ucl.ac.uk)

Last update: 21 May 2024

1. These datasets are only used for MSc dissertations as part of the Urban Spatial Science programme. Please do not use the datasets for other purposes and do not share the datasets with other people without permission from West Midlands Fire Services (WMFS).

2. Descriptions

   1. **wmfs_incidents.xlsx**: historical incident records

      1. call_time: timestamp of the fire incident, in format of dd/mm/yyyy hh:mm, e.g. 01/01/2009 00:00
      2. incident_classification_label: detailed label of incident
      3. incident_profile_label: another label of incident
      4. **incident_classification_level1**: type of incident, including levels of FALLS_RESPONSE, FALSE_ALARM, FIRE, OTHER, RTC, SSC. FALLS_RESPONSE is not a typo; it refers to calls that help people who fall. If the aim is to predict false alarms of fire, you can remove levels of FALLS_RESPONSE/OTHER/RTC/SSC (as they are not related to fire incidents) and keep only the levels of FIRE and FALSE_ALARM.
      5. prl_count: number of PRL engines sent for this incident
      6. brv_count: number of BRV engines sent for this incident
      7. EASTINGS: the easting coordinate under British National Grid projected coordinate system (EPSG:27700), in unit of meter. Note that the procedure of **geospatial obfuscation** has been applied to the original incident location in order to safeguard sensitive location data. That is, given an incidence with location (*x*, *y*) a random value *d* between 500m and 1000m and a random angle *a* between 0 and 360 is generated, this incidence is moved to the new location (*x* + *d* * sin *a*, *x* + *d* * cos *a*).
      8. NORTHINGS: the northing coordinate under British National Grid projected coordinate system (EPSG:27700), in unit of meter
      9. call_seconds: the time between the call being taken and the fastest vehicle being notified
      10. reaction_seconds: duration of reaction, i.e. the time between a resource being allocated for this incident and the resource getting ready
      11. driving_seconds: duration of driving from the fire station to the incident site

   2. **wmfs_mobilisations.xlsx**: this dataset contains all information of the wmfs_incidents, so it is not needed to link the two datasets.
      1. Incident_number: a reference number for incidents and can be linked to the row number of **wmfs_incidents.xlsx**. If two rows have the same incident_number then that means that there were multiple vehicles going to the same incident. This column is an unique number for each incident and should not be used to link to wmfs_incidents.
   
      2. resource_callsign: a unique key to identify which vehicle the row is referring to. 
         1. callsign_type: refers to the type of vehicle the row refers to. 
      3. call_time: the time when this call was made.
   
      4. call_seconds: refers to the time between the call being taken and that specific vehicle being notified (rather than the fastest).
   
      5. reaction_sections: the time between this vehicle being allocated for this incident and this vehicle getting ready.
   
      6. driving_seconds: duration of this vehicle driving from the fire station to the incident site.
   
      7. on_scene_seconds: duration of this vehicle on scene.
   
      8. EASTINGS: the easting coordinate of the incident, under British National Grid projected coordinate system (EPSG:27700), in unit of meter. 
   
      9. NORTHINGS: the northing coordinate of the incident, under British National Grid projected coordinate system (EPSG:27700), in unit of meter. 
   
3. **station_locations.csv**: locations and other attributes of each fire station at WMFS
      1. Station name: name of each station.
   2. Easting: the easting coordinate under British National Grid projected coordinate system (EPSG:27700), unit of meter
      3. Northing: the northing coordinate under British National Grid projected coordinate system (EPSG:27700), unit of meter
   4. PRL_Count: number of PRL (one type of fire engines) in this station.
      5. BRV_Count: number of BRV (one type of fire engines) in this station.
      6. Closed (Y/N): whether this station has been closed. N means the station is being used.
      7. Opened: ```can be ignored```.
      8. Closed: ```can be ignored```.
   
   4. **past_ia.csv**: past industry actions (or strikes) in WMFS
   
      1. Date: dd/mm/yyyy
      2. Time: hhmm-hhmm

3. Details of PRL and BRV

   1. a PRL (Pump Rescue Ladder) is a traditional fire truck and can attend all incident types. 

   2. A BRV (Brigade Response Vehicle) is a 4x4 vehicle that is dispatched to ‘lower’ risk incidents. The aim is increase the availability of the PRLs for more serious incidents such as house fires, which the BRV would not be as equipped to tackle.

   3. A PRL typically has 4-5 fire fighters, while a BRV typically has 2-4. 

   4. An image of one of WMFS BRVs is

      ![.](BRV.jfif)