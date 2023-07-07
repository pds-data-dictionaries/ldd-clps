PDS4 Commercial Lunar Payload Services Mission Dictionary User's Guide  
2023-07-07
Jennifer Ward


# Introduction
   1. Purpose of this User’s Guide
   - This User's Guide provides an overview of the CLPS Mission Data Dictionary. It details how to include the dictionary in a PDS4 label, describes the organization of classes and attributes, provides definitions of the classes and attributes, and lists examples of labels that use it. 
   1. Audience
   - This User's Guide should be useful to data providers intending to archive CLPS data with PDS as well as PDS Nodes who are working with these data providers.

# Overview of the CLPS Mission Dictionary

The CLPS Mission Dictionary contains classes, attributes, and rules specific to the CLPS missions and their instruments. 
Steward: Jennifer Ward, PDS Geosciences Node, geosci@wunder.wustl.edu

# How to Include the CLPS Mission Dictionary in a PDS4 Label

The dictionary consists of a set of files with names in the form PDS4_CLPS_xxxx_yyyy.ext, where
- xxxx = the PDS4 Information Model version, e.g. 1J00 
- yyyy = the CLPS Mission Dictionary version, e.g. 1000

and the file extensions are

- .csv = A comma-separated value table of dictionary attributes 
- .JSON = The dictionary contents in JSON format 
- .sch = The dictionary "rules" as an XML Schematron file 
- .txt = The report generated when the dictionary was built 
- .xml = The PDS4 label that describes this set of files 
- .xsd = The dictionary contents as an XML schema file

Only the schema and Schematron files are needed for validating a PDS4 label.

The latest version of this dictionary may be found on the PDS web site at https://pds.nasa.gov/datastandards/dictionaries/index-missions.shtml#clps.

The following is an example showing the use of this dictionary in a PDS4 label.

```
   <?xml version="1.0" encoding="UTF-8"?>
   <?xml-model href="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1J00.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
   <?xml-model href="https://pds.nasa.gov/pds4/mission/clps/v1/PDS4_CLPS_1J00_1000.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>    
   <Product_Observational xmlns="http://pds.nasa.gov/pds4/pds/v1"
       xmlns:clps="http://pds.nasa.gov/pds4/mission/clps/v1"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://pds.nasa.gov/pds4/pds/v1           https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1J00.xsd
                           http://pds.nasa.gov/pds4/mission/clps/v1   https://pds.nasa.gov/pds4/mission/clps/v1/PDS4_CLPS_1J00_1000.xsd">
```

The following is an example showing the location of the CLPS dictionary classes and attributes in a PDS4 label.

```
<Observation_Area>
    ...
       <Mission_Area>
        <clps:CLPS_Parameters>
          <clps:CLPS_Delivery_Information>
            <clps:nasa_delivery_name>
            <clps:vendor>
            <clps:vendor_mission_name>
            <clps:lunar_lander_name>
            <clps:project_scientist>
          </clps:CLPS_Delivery_Information>
          <clps:CLPS_Observation_Information>
            <clps:release_number>
            <clps:product_type>
            <clps:mission_phase_name>   
            <clps:spacecraft_clock_start>
            <clps:spacecraft_clock_stop>
            <clps:spacecraft_clock_partition>            
            <clps:producer_institution_name>
          </clps:CLPS_Observation_Information>
          <clps:NIRVSS_Parameters> 
          [Defined below]
          </clps:NIRVSS_Parameters>          
      </clps:CLPS_Parameters>
     </Mission_Area>
        ...         
```

The namespace for the CLPS Mission Dictionary is http://pds.nasa.gov/pds4/mission/clps/v1, abbreviated "clps:".

# Organization of Classes and Attributes

See the [schematic](../../CLPS_LDD_diagram.png) for a visual representation of the classes and attributes.

Below is a list showing the hierarchy of classes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

- CLPS_Parameters class
    - CLPS_Delivery_Information class
    - CLPS_Observation_Information class
    - NIRVSS_Parameters class

Below are lists showing the hierarchy of class attributes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

## CLPS_Parameters Class
- CLPS_Delivery_Information class
- CLPS_Observation_Information class

## CLPS_Delivery_Information Class
- nasa_delivery_name
- vendor
- vendor_mission_name
- lunar_lander_name
- project_scientist

## CLPS_Observation_Information Class
- release_number
- product_type
- mission_phase_name
- spacecraft_clock_start
- spacecraft_clock_stop
- spacecraft_clock_partition
- producer_institution_name

## NIRVSS_Parameters Class
- nirvss_aim_xscale
- nirvss_aim_yscale
- nirvss_aim_xstart
- nirvss_aim_xend
- nirvss_aim_ystart
- nirvss_aim_yend
- nirvss_led_illumination_duration

# Definitions

Classes (in alphabetical order)

*CLPS_Delivery_Information*
- The CLPS_Delivery_Information class provides information about a CLPS delivery.
- Minimum occurrences: 1
- Maximum occurrences: 1

*CLPS_Observation_Information*
- The CLPS_Observation_Information class provides information about a science observation.
- Minimum occurrences: 0
- Maximum occurrences: 1

*CLPS_Parameters*
- The CLPS_Parameters class is a superclass containing all CLPS mission classes.
- Minimum occurrences: 1
- Maximum occurrences: 1

*NIRVSS_Parameters*
- The NIRVSS_Parameters class provides metadata specific to NIRVSS observations.
- Minimum occurrences: 0
- Maximum occurrences: 1

Attributes (in alphabetical order)

*lunar_lander_name*
lunar_lander_name identifies the name of the lunar lander.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - Nova-C Lunar Lander - Nova-C Lunar Lander.
  - Peregrine Lunar Lander - Peregrine Lunar Lander.
  - Blue Ghost Lander - Blue Ghost Lander.
  - Griffin Lunar Lander - Griffin Lunar Lander.
  - SERIES-2 Lunar Lander - SERIES-2 Lunar Lander.
- Minimum occurrences: 1
- Maximum occurrences: 1
- Nillable: No

*mission_phase_name*
The mission_phase_name identifies a time period within the mission.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - CRUISE AND APPROACH - The cruise and approach phase takes place between launch and entry into Lunar Orbit. "Cruise" is also referred to 
          as "Transit" by some CLPS Vendors. This phase also includes Lunar Orbit Insertion (LOI). Some data products may be generated 
          during this time.
  - DESCENT AND LANDING - The descent and landing phase begins when the Lunar Orbit Phase is over, and the spacecraft has begun maneuvers 
          to land on the Lunar surface. This phase includes Powered Descent (PDI/PD) and Deorbit Decent and Landing (DDL).
  - LUNAR ORBIT - The Lunar Orbit phase begins when the spacecraft enters orbit around the moon. This phase includes Low Lunar 
          Orbit (LLO). The phase ends when the Descent and Landing phase begins.
  - SURFACE MISSION - The surface mission phase is the time from arrival on the moon through the end of the mission. Depending on the 
          mission, this may (or may not) include operations into the lunar night.
  - TEST, DEVELOPMENT, and CALIBRATION - The test, development, and calibration mission phase refers to the pre-launch period and consists of data 
          processing software development and testing, and instrument calibration. Some products generated during this phase may not be 
          a part of the final PDS archive but may be used for testing and peer review.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*nasa_delivery_name*
nasa_delivery_name identifies the delivery name assigned by NASA.
- PDS4 data type: ASCII_Short_String_Collapsed
- Valid values:
  - TO_2IM - NASA Task Order 2IM.
  - TO_2AB - NASA Task Order 2AB.
  - TO_PRIME1 - NASA Task Order PRIME1.
  - TO_19D - NASA Task Order 19D.
  - TO_20A - NASA Task Order 20A.
  - TO_CP11 - NASA Task Order CP11.
  - TO_CP12 - NASA Task Order CP12.
  - TO_CS3 - NASA Task Order CS3.
  - TO_CP21 - NASA Task Order CP21.
  - TO_CP22 - NASA Task Order CP22.
- Minimum occurrences: 1
- Maximum occurrences: 1
- Nillable: No

*nirvss_aim_xend*
Pixel location of the largest value column of the sub-array. Always given in the native Scale 0. Allowable values are from 0 to 2047.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2047

*nirvss_aim_xscale*
Scale factor representing the number 2^N of columns that are averaged onboard by the AIM, where N is the scale factor. For each scale factor, the number of columns is 
decreased by 1/(2^N) of the native number of columns (2048): for XScale = 0 the image contains the native number of columns; for XScale = 1 the image contains 1/2 of the 
native number of columns; etc. Allowable values of XScale are 0, 1, 2, 3, 4.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 4

*nirvss_aim_xstart*
Pixel location of the smallest value column of the sub-array. Always given in the native Scale 0. Allowable values are from 0 to 2047.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2047

*nirvss_aim_yend*
Pixel location of the largest value row of the sub-array. Always given in the native Scale 0. Allowable values are from 0 to 2047.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2047

*nirvss_aim_yscale*
Scale factor representing the number 2^N of rows that are skipped onboard by the AIM, where N is the scale factor. For each scale factor, the number of rows is decreased by 
1/(2^N) of the native number of rows (2048) for YScale = 0 the image contains the native number of rows; for YScale = 1 the image contains 1/2 of the native number of rows; 
etc. Allowable values of YScale are 0, 1, 2, 3, 4.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 4

*nirvss_aim_ystart*
Pixel location of the smallest value row of the sub-array. Always given in the native Scale 0. Allowable values are from 0 to 2047.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2047

*nirvss_led_illumination_duration*
Time, in milliseconds, that the chosen LED is in the illuminated or on state. Typically LED illumination duration time equals the image exposure duration. However, when the 
image exposure duration exceeds the LED's maximum allowable exposure, the LED will turn off at the maximum allowable exposure, while the detector continues acquiring the image.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Unit of measure type: Units_of_Time

*producer_institution_name*
The producer_institution_name specifies the identity of the facility or institution that produced the product.
- PDS4 data type: ASCII_Short_String_Preserved
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*product_type*
The product_type element identifies a group of data products within a collection that have some property in common, such as processing level, resolution, or instrument-specific 
setting.
- PDS4 data type: ASCII_Short_String_Collapsed
- Valid values:
  - NSS_ENG_CAL - Time sequenced NSS engineering data (engineering units: voltages, circuit board temperatures; high voltage and 
          discriminator threshold settings).
  - NSS_ENG_RAW - Time sequenced NSS engineering data (raw engineering: encoded parameters that are translated to engineering units 
          by processing).
  - NSS_SCI_CAL - NSS processed neutron count rates and affiliated instrument data (time stamped).
  - NSS_SCI_RAW - NSS raw neutron count rates and affiliated instrument data (time stamped).
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*project_scientist*
The project_scientist element identifies the name of the delivery's Project Scientist.
- PDS4 data type: ASCII_Short_String_Preserved
- Minimum occurrences: 1
- Maximum occurrences: 1
- Nillable: No

*release_number*
release_number is the identifier of a scheduled release of data from PDS. The first data release has release_number "0001". The release_number for a given product is always the 
first release in which it appears, and does not change if the product is revised later.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum characters: 4

*spacecraft_clock_partition*
The spacecraft_clock_partition provides the clock partition active for the spacecraft_clock_start and spacecraft_clock_stop attributes. This attribute may be used when the 
spacecraft_clock values do not include a partition number.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 1

*spacecraft_clock_start*
The spacecraft_clock_start attribute provides the value of the spacecraft clock at the beginning of a time period of interest.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum characters: 1
- Maximum characters: 19
- Pattern: ([1-9]/)?[0-9]{1,10}(\.[0-9]{1,9})?

*spacecraft_clock_stop*
The spacecraft_clock_stop_count attribute provides the value of the spacecraft clock at the end of a time period of interest.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum characters: 1
- Maximum characters: 19
- Pattern: ([1-9]/)?[0-9]{1,10}(\.[0-9]{1,9})?

*vendor*
The vendor element identifies the company responsible for delivering the payload to the lunar surface.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - Astrobotic - Vendor is Astrobotic.
  - Draper - Vendor is Draper.
  - Firefly Aerospace - Vendor is Firefly Aerospace.
  - Intuitive Machines - Vendor is Intuitive Machines.
- Minimum occurrences: 1
- Maximum occurrences: 1
- Nillable: No

*vendor_mission_name*
vendor_mission_name identifies the name given to the mission by the CLPS vendor.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - Blue Ghost 1 - Mission is Blue Ghost 1 (BG1).
  - Griffin Mission One - Mission is Griffen Mission One (GM1).
  - Intuitive Machines Mission 1 - Mission is Intuitive Machines Mission 1 (IM1).
  - Intuitive Machines Mission 2 - Mission is Intuitive Machines Mission 2 (IM2).
  - Intuitive Machines Mission 3 - Mission is Intuitive Machines Mission 3 (IM3).
  - Peregrine Mission 1 - Mission is Peregrine Mission 1.
- Minimum occurrences: 1
- Maximum occurrences: 1
- Nillable: No


# Examples

Example PDS4 label snippet for CLPS NSS calibrated engineering data product:

```
       <Mission_Area>
         <clps:CLPS_Parameters>
          <clps:CLPS_Delivery_Information>
            <clps:nasa_delivery_name>TO_2AB</clps:nasa_delivery_name>
            <clps:vendor>Astrobotic</clps:vendor>
            <clps:vendor_mission_name>Peregrine Mission 1</clps:vendor_mission_name>
            <clps:lunar_lander_name>Peregrine Lunar Lander</clps:lunar_lander_name>
            <clps:project_scientist>Paul Niles</clps:project_scientist>
          </clps:CLPS_Delivery_Information>
          <clps:CLPS_Observation_Information>
            <clps:release_number>0001</clps:release_number>
            <clps:product_type>NSS_ENG_CAL</clps:product_type>
            <clps:mission_phase_name>SURFACE MISSION</clps:mission_phase_name>         
            <clps:producer_institution_name>Applied Physics Laboratory</clps:producer_institution_name>
          </clps:CLPS_Observation_Information>
         </clps:CLPS_Parameters>
       </Mission_Area>
```
