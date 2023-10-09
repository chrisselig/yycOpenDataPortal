# yycOpenDataPortal
The goal of this project is to pull various data sets together relating to Calgary to help information decisions like where to rent an apartment or buy a house. This data goes beyond data normally found on MLS or Rentfaster and includes things like crime statistics, demographics, location of fire stations, EMS and Police locations.

# Architecture
Azure will be the cloud provider used. Below is what the high level architecture will look like.

![arch](https://github.com/chrisselig/yycOpenDataPortal/blob/main/00_Architecture/high%20level%20architecture.png)

Using Azure Data Factory (ADF) data will be extracted from REST APIs on a monthly basis (mostly, anyway) and loaded to the Azure data lake. No transformations are performed at this stage.

The data is then moved to Synapse, into bronze stage. No transformations take place here.

Moving into the silver stage, some basic transformations take place, like column renaming, working with data types.

Finally, the data is moved to gold stage, where it is fully transformed into a star schema design.

# Data Model - Star Schema

End result is a star schema, with a fact table for community disorder statistics and multiple dimensions.

![starschema](https://github.com/chrisselig/yycOpenDataPortal/blob/main/00_data_modeling/star_schema.png)

# Analysis

Preliminary analysis takes place using Python/SQL/Databricks

Final visualization is completed using Power BI.


# Future Roadmap
More and more datasets to be added
Switch the dashboard from Power BI to something more robust. Probably going to be R Shiny.
