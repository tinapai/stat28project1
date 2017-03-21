This is a shortened version of my Stat 28 (Statistical Methods in Data Science) midterm project. The overarching goal of this project is to evaluate how the the amount a patient has to pay (i.e. after Medicare) change for different regions or urban/rural areas of the country. I look at the amount patients pay and what percentage of the treatment cost the patients pay for Chronic Obstructive Pulmonary Disease (COPD), heart failure, fractures, and diabetes. I do some basic exploration of the data using plots and summaries, and then I examine how the costs differ across different regions urbanization levels. For my hypothesis testing, I took a permutation test function from class material and wrote my own bootstrap confidence interval function rather than finding existing packages from online because I wanted to demonstrate understanding of the implementation of these concepts.

Here are the descriptions of the data set variables that I used, taken from the project description.

* DRG.Definition: Name of diagnosis [Diagnosis-related group=DRG]. "CC" added to the end stands for complication or comorbidity due to the diagnosis and "MCC" stands for a major complication or comorbidity.
* Average.Total.Payments: "The average total payments to all providers for the MS-DRG including the MS-DRG amount, teaching, disproportionate share, capital, and outlier payments for all cases. Also included in average total payments are co-payment and deductible amounts that the patient is responsible for and any additional payments by third parties for coordination of benefits." You can interpret this variable as the total amount that paid by the Medicare and patients to the hospitals
* Average.Medicare.Payments: "The average amount that Medicare pays to the provider for Medicare's share of the MS-DRG. Average Medicare payment amounts include the MS-DRG amount, teaching, disproportionate share, capital, and outlier payments for all cases. Medicare payments DO NOT include beneficiary co-payments and deductible amounts nor any additional payments from third parties for coordination of benefits." You can interpret this variable as the amount paid by the Medicare. The difference between Average.Medicare.Payments and Average.Total.Payments will will assume to be the average amount paid by the patients at that hospital.
* regions: A variable created for this project that classifies the hospital into one of four regions of the
US ("midwest","northeast","south", and "west"). These classifications were made based on the state in which the hospital is located.
* Urban: A variable created by for this project that classifies the hospital into their level of rural versus urban. We rely on the Census Bureau which divides the country into regions and assigns those regions one of three values:
- Urbanized Areas (UAs) of 50,000 or more people;
- Urban Clusters (UCs) of at least 2,500 and less than 50,000 people.
- Rural encompasses all population, housing, and territory not included within either of the above urban areas.
The Census Bureau also identifies which of these three types of areas are covered by any zipcode. Thus we assigned each hospital to these areas based on the zip-code in which the hospital is located. However, a zip code frequently covers more than one such region. Therefore the following codes are given in the variable Urban:
- 1 = only rural regions in the zipcode
- 2 = combination of rural and Urban Clusters in the zipcode
- 3 = only Urban Clusters in the zipcode
- 4 = combination of Urban Clusters and Urbanized Areas in the zipcode
- 5 = only urbanized Areas in the zipcode
- 0 = a mix of Urbanized Areas and Rural (and perhaps also Urban Clusters) in the zipcode

