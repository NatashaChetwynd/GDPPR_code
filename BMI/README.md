# BACKGROUND
BMI is of particular interest in relation to the COVID-19 pandemic therefore NHS Digital have written some code to understand the quality, coverage, and distribution of BMI recording within the GDPPR dataset.

BMI category can be recorded via six methods within GDPPR, all of which use SNOMED codes within patient journal tables:

1.	Snomed codes for BMI values e.g. code for ‘Body mass index (observable entity)’ with an associated value of 18.5
2.	Snomed codes for BMI categories (no values) e.g. code with description of ‘Obese (finding)’
3.	Snomed codes for height and weight values 
4.	Snomed codes for child BMI centiles/categories (no values) e.g. code with description of ‘Child body mass index 10th-24th centile (finding)’
5.	Snomed codes for child BMI values e.g. code for ‘Body mass index (observable entity)’ with an associated value of 18.5 for a patient below the age of 18 at the date of the journal
6.	Snomed codes for child height and weight values

Please note that methods 4, 5 and 6 for children are separated out because their BMI categories are calculated using centiles which are based on their sex, age and BMI (or height and weight calculated BMI).

The code accounts for all six of these methods and produces a BMI category using [NHS BMI groupings](https://www.nhs.uk/live-well/healthy-weight/bmi-calculator/). Please note that cut off points for outliers e.g. cut off low BMI at 10 and high at 55, were determined through initial analyses and were agreed with internal clinicians. Cut off points were deemed to be necessary as we can’t be sure without further analysis whether values outside of the chosen range are DQ issues or just outliers.

# NOTES

GDPPR data = ```gdppr_cur_clear.vw_gdppr```

BMI snomed codes reference data = ```ref_data.BMI_CODES```

Height snomed codes reference data = ```ref_data.HEIGHT_CODES```

Weight snomed codes reference data = ```ref_data.WEIGHT_CODES```

Child BMI centiles reference data = ```ref_data.child_bmi_centiles_ordered ```

_Please note that the child centile reference data is avilable from the [Royal College of Paediatric and Child Health](https://www.rcpch.ac.uk/resources/body-mass-index-bmi-chart) and requires a (free) license so is not included within this repository. If you are unable to obtain child centile reference data then it is not possible to accurately categorise a child's BMI._
