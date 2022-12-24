# Flu Risk Assessment Project

## Summary

I began this analysis based on a request to find out how to better allocate temporary medical staff across the United States during flu season. This analysis looks at flu hospitalization risk across the country as it evolves throughout the year. This examines not just flu deaths, but also influenza lab test, clinic visits, and age demographics.

I began by examining yearly flu deaths from 2011 to 2017, showing that the seasonality of the flu is roughly the same each year, peaking in January and hitting a low point in the summer. We also show that most of the deaths are among older populations.

After that, I looked at the key indicators for flu risk by state and month, normalized by population: flu deaths, positive lab tests, clinic visits for flu-like illnesses, and percent of population over 65.

Finally, I combined these indicators into a risk index (see methodology below) for each state and each month of the year.

Using insights from the risk index visualization, I determined which states are at the highest risk per capita for flu hospitalization and make recommendations on medical staff allocation accordingly.

## Findings

[View the analysis here on Tableau](https://public.tableau.com/app/profile/forrest.roth/viz/FluDeaths_16619865638940/Story1)

## Datasets used

Influenza deaths by geography, time, age, and gender (Source: CDC)

https://wonder.cdc.gov/ucd-icd10.html


Population data by geography (Source: U.S. Census Bureau)

https://coach-courses-us.s3.amazonaws.com/public/courses/data-immersion/A1-A2_Influenza_Project/Census_Population_transformed_202101.csv


Counts of influenza laboratory test results by state (survey)

https://gis.cdc.gov/grasp/fluview/fluportaldashboard.html (Source: CDC)

## Data Limitations

The ideal data for determining staffing needs would have been actual hospitalizations and health care system load, ideally at the hospital-level.

Even the datasets used had some limitations that affected the analysis. If the flu deaths dataset had been complete (even including death statistics for when there were 9 or fewer deaths in a given state and month), then there would have been more accurate representation of small states and less vulnerable age groups.

The lab tests and clinic visits data seemed to vary quite a bit between states and times of year, suggesting that the reporting was not consistent across state and month.

For all 3 CDC datasets, there was data missing for certain states. This almost certainly skewed the risk index to make it less reliable for these states.

<sup>Alaska: No influenza deaths data; Florida: No lab tests or clinic visits data; New Jersey: No lab tests data; Rhode Island: No lab tests data;
Vermont: No influenza deaths data</sup>

## Risk Index methodology

To come up with an index between 0 and 1 to measure risk in each state and each month, we averaged four values per capita for the years 2011-2014 (years when data was most complete):

- Influenza deaths
- Positive lab tests
- Clinic visits for influenza-like-illnesses
- Vulnerable population (% population over 65)

I then assigned a weight to each value, based on how well I thought each value represented risk:
- Deaths: 50%
- Lab tests: 12.5%
- ILI visits: 12.5%
- Vulnerable population: 25%

Some states did not have influenza death data, and some did not have lab test and/or ILI visits data.1 For these states, the weights were as follows:
- No deaths data: Tests: 37.5%, Visits 37.5%, Population 25%
- No lab tests or no visits data: Deaths: 60%, Tests/Visits 15%, Population 25%
- No lab tests and no visits data: Deaths: 75%, Population 25%

Deaths were always weighted more since the data seemed to be the most comprehensive and reliable. Population was weighted the same for all states to make sure to not skew the data for states that were missing data, since vulnerable populations stayed the same throughout the year.
