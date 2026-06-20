# MRLF-DATA FELLOW CONSTITUENCY ANALYSIS
This repository was created to share my data analysis of Meghalaya's constituencies.
The dataset that was used in this analysis was the sample data that was provided by the organisation comprising of 60 constituencies of Meghalaya.The data was analysed as per section wise.
__________________________________________________________________________________________________________________

# Section 1 — Data Audit 

1. Loading data: In this section,the data was analysed in R and Excel subsequently.I first load the data in R to perfrom Descriptive statistics (mean, median, minimum, maximum, stdard deviation) of 8 numerical variables of my choice. For this analysis, I have chosen **(i).Total_Households	(ii).Electorate 2023	(iii).BPL Households Count, (iv).MGNREGS Active Job Cards, (v).PM Awas Yojana Sanctioned, (vi).Health Sub Centres, (vii).Govt Primary Schools, (viii).PM KISAN Beneficiaries**. The variables chosen for this particular analysis are raw count data. I first analysed the descriptive statistics of the data in Excel after which i run them in R. I cross checked both the results for data accuracy.

2. Identification of data quality issues — I inspected the sample file and after which I have created a file of just 8 numerical column and it looks generally clean structurally, but there are a few things that caught my attention that are worth checking before I proceed with the analysis. There are No missing values or duplicate records,every data is unique. The file has 60 rows and 28 columns and there are no nulls and no duplicated rows.
However, there are certain noteworthy outlier in **Total Households and Electorate 2023.** These two variables show the most outlier flags by Inter Quartile Range. A handful of constituencies have much larger values than the rest, especially Constituencies like Shillong Cantonment, Tura, North Tura, Pynthorumkhrah, and Jowai.Although the data for this assignment was curated, the data from these constituencies are large and demands thorough analysis.Two columns were added derived from the dataset :_**Voters per household and BPL household share**._

 Voters per household will help us compare how electorally dense each constituency is and BPL household share provides a standardized poverty burden measure, which is better than raw counts when comparing constituencies of different sizes.The new columns essentially has two additional numerical  normalized variable where Mawlai has about 7.03 Voters per household, BPL household share of about 0.26, and subsequently for the rest of the 60 constituencies was calculated. All of these calculations were carried out in Excel. 

_________________________________________________________________________________________________

# Section 2 — Analytical Deep-Dive 
1. Regional disparities - Comaprison between Khasi Hills, Jaintia Hills, and Garo Hills on Water access (JJM), Road infrastructure, and Literacy	                 **Khasi Hills** - _JJM functional tap connections (61.4%),Road length km (144.68km), Pucca road (63.05%) and Literacy rate (77.7%)_ ; **Jaintia Hills**	- _JJM functional tap connections (46.9%),Road length km (170.6km), Pucca road (49.92%) and Literacy rate (73.1%)_ ; **Garo Hills** -_JJM functional tap connections (43.4%),Road length km (173.7km), Pucca road (56.19%) and Literacy rate (74.0%)_.

**Water access**- On JJM functional tap connections, Garo Hills is worst off at about 43.4%, followed by Jaintia Hills at 46.9%. Khasi Hills is clearly ahead at 61.4%. So if we focus only on household water access, Garo Hills is the most underserved region.
**Road infrastructure**- Road infrastructure shows a more mixed story because there are two different measures here. On total road length, Khasi Hills has the lowest average at about 144.68 km, compared with 170.6 km in Jaintia Hills and 173.7 km in Garo Hills. But lower road length does not automatically mean worse infrastructure, because regions can differ in size and terrain.
**Pucca road share**, which is usually the better quality indicator, Jaintia Hills is the weakest at 49.92%, compared with 56.19% in Garo Hills and 63.05% in Khasi Hills. So for road quality, Jaintia Hills is the most underserved.
Literacy- For literacy rate, Jaintia Hills again ranks lowest at 73.1%, slightly below Garo Hills at 74.0%, and well below Khasi Hills at 77.7%.
So on education outcomes, Jaintia Hills is the most underserved.
Which region is most underserved?
If we judge overall across water, road quality, and literacy, the answer is:
Jaintia Hills is the most underserved overall.
That’s because it is the lowest on pucca road coverage and lowest on literacy, and it also has below-average water access.
However, there is one important exception:
Garo Hills is the most underserved specifically on water access, since it has the lowest JJM coverage.
 
2. Scheme delivery gaps Jal Jeevan Mission and PM Awas Yojana- Constituencies with the lowest scheme delivery.
**Lowest JJM coverage**: The weakest constituencies on Jal Jeevan Mission functional tap coverage are: Resubelpara(23.4%), Khliehriat (24.1%), Kharkutta (24.1%), Sohiong (26.6%), Mawhati (26.7%), Mendipathar (27.1%), Selsella (27.4%), Mawphlang (27.4%), Songsak (27.6%), Williamnagar (28.2%).

**Lowest PM Awas completion**
The weakest constituencies on PM Awas completion are: Sohiong (46.9%), East Shillong (48.0%), Mahendraganj (49.3%),Mawryngkneng (49.6%),Gambegre (50.3%),Selsella (51.4%), Shillong West (52.5%), Shillong North (53.4%),Mawphlang (53.9%), Ranikor (55.6%). **Repeated laggards across both schemes**: A few constituencies show up as weak performers in both: Sohiong, Selsella, Mawphlang.

When we look at the **Geographic pattern** of these data ,we found that the average delivery by region shows a visible pattern-
**Garo Hills**- JJM average: 43.4%, PM Awas average: 71.0% ; **Jaintia Hills**-JJM average: 46.9%, PM Awas average: 77.3%, **Khasi Hills**- JJM average: 61.4%, PM Awas average: 69.9%.
What we know from the data is that, JJM weakness is concentrated more in Garo Hills and parts of Jaintia Hills.Khasi Hills performs much better on JJM on average, though it still has some PM Awas laggards. PM Awas weakness is more mixed geographically, several of the bottom constituencies are in Khasi Hills, but South West / West Garo Hills also contribute lagging constituencies

**By district**
District averages shows the pattern further:
Weakest districts for JJM- North Garo Hills (32.4%), East Garo Hills (34.1%), South West Garo Hills (42.1%), East Jaintia Hills (42.2%)
Weakest districts for PM Awas- South West Garo Hills (56.9%), East Khasi Hills (68.3%), West Khasi Hills (69.1%), North Garo Hills (69.2%).
The Bottom line on geography is that, _there is a geographic pattern_. JJM underperformance is strongly clustered in the Garo belt, especially North and East Garo Hills, PM Awas underperformance is less regionally concentrated and appears in both Khasi and Garo constituencies, East Khasi Hills has several PM Awas laggards despite relatively stronger JJM performance overall.

**BPL concentration correlation with scheme delivery**
When I look at data related to BPL household concentraion and scheme delivery, I used the following seven (7) variables, i).BPL Households Pct	, ii).JJM Functional Tap Connections Pct, iii).PM Awas Completion_Pct, iv).Literacy Rate Pct, v).Pucca Road Pct, vi).Internet 4G Coverage Pct, vii).Road Length Km. For this test, I employ Spearman's Rank correlation and OLS regression.I test to check whether there is a monotonic relationship between the two variables, meaning whether ,when one variable increases, does the other tend to increase or decrease.
I test for the relationship between _BPL vs JJM and BPL vs PMAY_. My analysis found that BPL vs JJM the correlation is about -0.43, showing a moderate negative relationship between BPL and JJM, meaning, as BPL increases, JJM tends to decrease, or vice versa. The p-value is 0.00062, which is very small and well below the common threshold of 0.05. So this relationship is _statistically significant_. In essence, this means the negative relationship is unlikely to be due to random chance.When I test for the correlation between BPL vs PMAY, I found that BPL vs PMAY correlation is about 0.048, which is very close to zero, meaning that there is almost no linear relationship between BPL and PMAY in my data. The p-value is 0.713, which is much larger than 0.05. So this relationship is _not statistically significant_. In plain English, there is no strong evidence of a real linear association between these two variables.
<img width="2368" height="1765" alt="BPL_vs_JJM_Correlation" src="https://github.com/user-attachments/assets/e20ac79f-c6d9-4094-beab-080d4c2e5cf4" />
<img width="2368" height="1765" alt="BPL_vs_PMAY_Correlation" src="https://github.com/user-attachments/assets/b6e8627f-0b5c-4639-a4aa-4b21ee67a161" />


  3.**Fund utilisation** - The 5 constituencies with the lowest Constituency Development Fund utilisation are: Shangpung (35.3%), Gambegre (35.6%), Raksamgiri (36.8%), Mahendraganj (37.5%), Sohra (40.1%).A few observations were seen as per the data,where we found regional pattern, with _3 of the 5_ regions are in Garo Hills, 1 is in Jaintia Hills, and 1 is in Khasi Hills.So the underutilisation is not random - it appears more concentrated in Garo Hills and other less urban / harder-to-service areas. These 5 constituencies have consistently high BPL shares- Shangpung (44.0%), Gambegre (42.6%), Raksamgiri (43.1%),Mahendraganj (47.7%), Sohra (55.0%). For context, the average BPL in the dataset  is about 38.46%. So all five are above average, and Sohra is especially high.

**Weak infrastructure tends to coincide with low utilisation**- Compared with the dataset average, these constituencies generally show :Lower tap-water coverage, Lower 4G coverage, weak road connectivity.The dataset averages shows that, JJM tap connections (52.4%), Pucca road share (58.2%), 4G coverage (51.7%).
For context, **Shangpung** - JJM 29.1%, roads 49.6%, 4G 43.8%; **Mahendraganj** - JJM 51.7%, roads 48.0%, 4G 26.5% ; **Raksamgiri** - 4G only 50.8%, though roads are somewhat better at 70.4% ,**Sohra** - roads are decent at 69.4%, but 4G is only 45.4% and BPL is very high ,**Gambegre** - roads 57.9%, 4G 69.0%, but tap coverage still low at 46.1%.  So the broad pattern is: _higher poverty -> patchier physical and digital infrastructure->lower fund utilisation._

This suggests that the lowest-utilisation constituencies are often places where, project execution is probably harder, contractor/logistics capacity may be weaker, beneficiary identification and approvals may take longer, and implementation bottlenecks are more severe.

A plausible hypothesis from the data is that:
_**Underutilisation of Funds for Development is being driven less by lack of need and more by implementation constraints in poorer, harder-to-connect constituencies**_.

More specifically, places with high BPL populations,weaker connectivity, lower service coverage,and likely more dispersed or difficult terrain across the state
may struggle to convert allocations into completed projects because of: _procurement delays, limited local administrative capacity, contractor shortages, transport/logistics challenges, weaker monitoring due to poor digital connectivity_.

<img width="3570" height="1770" alt="05_Fund_Risk" src="https://github.com/user-attachments/assets/5e5527a7-48a5-43f1-93ca-9b315d960ef1" />



  4.**My own Findings**: For this part, i analysed data related to Health and Education as most of the earlier analysis have covered extensively on schemes and infra. The following variables are used for this analysis- _i).Primary_Health_Centres, ii).Community_Health_Centres, iii).Govt_Primary_Schools, iv).Govt_Secondary_Schools, v).Literacy_Rate_Pct, vii).Internet_4G_Coverage_Pct._

What i discovered was that,these variables do not all move together. In other words, a constituency with more schools or health centres does not automatically show higher literacy or better internet coverage.

**Education** - Across the 60 constituencies: Primary Health Centres average about 3.75 per constituency, Community Health Centres average about (1.03), Govt Primary Schools average about (35), Govt Secondary Schools average about (12),Literacy rate averages (75.6%), 4G coverage averages (51.7%). The biggest variation is in internet coverage and literacy, especially 4G coverage, which ranges from 18.1% to 96.9%. That tells me connectivity is much more uneven than the counts of institutions.

_Regional pattern_: At the regional level, Khasi Hills performs best on the two outcome-style indicators: Literacy about (77.7%), 4G coverage about (55.8%)
Compared with- Garo Hills literacy (74.0%, 4G 47.7%), Jaintia Hills literacy (73.1%, 4G 48.7%).

The data shows that, Khasi Hills has a relative edge in human-capital and digital-access indicators. Interestingly, Jaintia Hills has the highest average secondary school count at about 14.3, but still lower literacy than Khasi Hills. That again reinforces the point that institution count alone is not enough to explain literacy differences.

A very interesting pattern is that some constituencies have above-median 4G coverage but below-median literacy.
Examples include: Raliang - literacy (65.2%, 4G 70.9%) ; Gambegre - literacy (63.7%, 4G 69.0%) ; Bajengdoba - (literacy 58.9%, 4G 64.2%). 
This is worth noting because it breaks the general trend.

And what I think might explain it is that , telecom access may have improved faster than education outcomes, literacy changes slowly over time, while connectivity can expand quickly, these could be places where infrastructure has arrived, but educational attainment is still catching up, digital access may not yet be translating into educational gains because of affordability, device ownership, or quality-of-use gaps. So this is a classic case of infrastructure availability not yet becoming social outcome improvement. 

**Health care** - Health infrastructure appears uneven but not clearly aligned with literacy/connectivity
Community_Health_Centres vary only from 0 to 2, so the range is narrow. That makes it harder to see strong statistical relationships. Primary_Health_Centres range from 1 to 6, but again show almost no clear relationship with literacy or internet coverage.
My analysis is that health facility counts here are probably being driven more by administrative planning norms, geography and remoteness, service catchment design
rather than by the same forces driving literacy and digital connectivity.
The Bottom line is that, among these indicators, literacy and 4G coverage move together much more clearly than literacy does with counts of schools or health centres,and the most useful anomaly to flag is this, that some constituencies already have relatively strong 4G coverage but still low literacy, suggesting that digital infrastructure is outpacing social development outcomes.
<img width="940" height="704" alt="image" src="https://github.com/user-attachments/assets/57aef0f2-e9aa-4bce-b838-7a58cb0ac604" />


____________________________________________________________________________________________________________________________________________

# Section 3 — Constituency Profile Generator 
As directed, I have analysed this particular step in Jupyter notebook (where i also make use of AI tools to debug codes).
The following constituency profile was analysed and created: Constituency snapshot, Scheme status, Infrastructure , Benchmarking,and 
Fund utilisation flag.
The file was uploaded and shared in my repository and can be viewed by all. 

____________________________________________________________________________________________________________________________________________

# Section 4 — Bonus: Interactive Dashboard 

An interactive dashboard was build using Power BI supporting, Filtering by region and district, Displaying 3 indicators side-by-side for a selected constituency, Highlighted the bottom 5 and top 5 constituencies Education, Scheme delivery gaps and Health care.


