# MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS
This repository was created to share my data analysis of Meghalaya's constituencies.
The dataset that wa sused in this analysis was the sample data that was provided by the organisation comprising of 60 constituencies of Meghalaya.The data was analysed as per section wise.
__________________________________________________________________________________________________________________

# Section 1 — Data Audit 

1. Loading data: In this section,the data was analysed in R and Excel subsequently.I first load the data in R to perfrom Descriptive statistics (mean, median, minimum, maximum, stdard deviation) of 8 numerical variables of my choice. For this analysis, I have chosen **(i).Total_Households	(ii).Electorate 2023	(iii).BPL Households Count, (iv).MGNREGS Active Job Cards, (v).PM Awas Yojana Sanctioned, (vi).Health Sub Centres, (vii).Govt Primary Schools, (viii).PM KISAN Beneficiaries**. The variables chosen for this particular analysis are raw count data. I first analysed the descriptive statistics of the data in Excel after which i run them in R for accuracy of the results. I cross checked both the results for data accuracy.

2. Identification of data quality issues — I inspected the sample file and after which I have created a file of just 8 numerical column and it looks generally clean structurally, but there are a few things that caught my attention that are worth checking before I proceed with the analysis. There are No missing values or duplicate records,every data is unique. The file has 60 rows and 28 columns and there are no nulls and no duplicated rows.
However, there are certain noteworthy outlier in **Total Households and Electorate 2023.** These two variables show the most outlier flags by Inter Quartile Range. A handful of constituencies have much larger values than the rest, especially Constituencies like Shillong Cantonment, Tura, North Tura, Pynthorumkhrah, and Jowai.Although the data for this assignment was curated, the data from these constituencies are large and demands thorough analysis.
3. Two columns were added derived from the dataset :**Voters per household and BPL household share**.Voters per household will help us compare how electorally dense each constituency is and BPL household share provides a standardized poverty burden measure, which is better than raw counts when comparing constituencies of different sizes.The new columns essentially has two additional numerical  normalized variable where Mawlai has about 7.03 Voters per household, BPL household share of about 0.26, and subsequently for the rest of the 60 constituencies was calculated. All of these calculations were carried out in Excel. 


   


The Results of the Descriptive statistics of the 8 numerical variables are here:

