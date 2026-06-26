# MRLF-DATA FELLOW CONSTITUENCY ANALYSIS
This repository was created to share my data analysis of Meghalaya's constituencies.
The dataset that was used in this analysis was the sample data that was provided by the organisation comprising of 60 constituencies of Meghalaya.The data then were analysed as per section wise and the findings are also presented subsequently.

_**Note on the Use of Analytical Tools and AI:**_
_For the purpose of this analysis, descriptive statistics were first calculated manually in Excel and subsequently verified in R to ensure data accuracy. Correlation and regression analyses were conducted in Jupyter Notebook, while Power BI was used to generate the dashboards. AI tools were also utilised to assist with syntax error correction, specifically for the analysis in Section 3._
__________________________________________________________________________________________________________________

# Section 1 — Data Audit 
1.**Loading data**: In this section, the data was analysed in R and Excel. Subsequently, I first load the data in R to perfrom Descriptive statistics (mean, median, minimum, maximum, standard deviation) of 8 numerical variables of my choice. For this analysis, I have chosen **(i).Total_Households (ii).Electorate 2023	(iii).BPL Households Count, (iv).MGNREGS Active Job Cards, (v).PM Awas Yojana Sanctioned, (vi).Health Sub Centres, (vii).Govt Primary Schools, (viii).PM KISAN Beneficiaries**. The variables chosen for this analysis are raw count data, and all of these variables are representative of the Human Development Index through which we can assess the average achievement in key dimensions of human development. I first analysed the descriptive statistics of the data in Excel, and after which i run them in R. I cross checked both the results for data accuracy.

Click here for the code that was used to run this test in R:
- <a href="https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/Data%20Loading%20%26%20Descriptive%20statistics.txt"> Data Loading code in R</a>

2.**Identification of data quality issues** — I inspected the sample file, and after which I have created a file of just 8 numerical column and it looks generally clean structurally, but there are a few things that caught my attention that are worth checking before I proceed with the analysis. There are No missing values or duplicate records, every data is unique. The file has 60 rows and 28 columns and there are no nulls and no duplicated rows. However, there are certain noteworthy outlier in **Total_Households** and **Electorate_2023**. These two variables show the most outlier flags by Inter Quartile Range. A handful of constituencies have much larger values than the rest, especially Constituencies like Shillong Cantonment, Tura, North Tura,Pynthorumkhrah and Jowai.

3.Two columns were added derived from the dataset : _**Voters per household**_ and **_BPL household share_**.

Voters per household will help us compare how electorally dense each constituency is and BPL household share provides a standardized poverty measure, which is better than raw counts when comparing constituencies of different sizes.The new columns essentially has two additional numerical  normalized variable where Mawlai has about 7.03 Voters per household, BPL household share of about 0.26, and subsequently for the rest of the 60 constituencies was calculated. All of these calculations were carried out in Excel. 

The dataset that was used in this section 1 of the analysis is avalaible here:
 - <a href="https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/DATA%20SECTION%201%20with%20two%20derived%20columns.csv"> Dataset with 8 numerical variables</a>

The results of the descriptive statistics of the 8 variables in this analysis is provided below:
| variable                  | n  | mean     | sd       | median | min   | max   | range |
| ------------------------- | -- | -------- | -------- | ------ | ----- | ----- | ----- |
| Total_Household           | 60 | 4343.15  | 2293.832 | 3514   | 1629  | 11211 | 9582  |
| Electorate_2023           | 60 | 29844.72 | 14857.29 | 24943  | 11305 | 63978 | 52673 |
| BPL_Households_Count      | 60 | 1503.833 | 537.5621 | 1360   | 491   | 2892  | 2401  |
| MGNREGS_Active_Job_Cards  | 60 | 850.95   | 425.5362 | 852.5  | 120   | 1987  | 1867  |
| PM_Awas_Yojana_Sanctioned | 60 | 227.3    | 107.1823 | 199.5  | 89    | 506   | 417   |
| Health_Sub_Centres        | 60 | 8.683333 | 4.848525 | 8      | 2     | 18    | 16    |
| Govt_Primary_Schools      | 60 | 34.95    | 13.53392 | 36.5   | 8     | 55    | 47    |
| PM_KISAN_Beneficiaries    | 60 | 749.2833 | 336.3872 | 735    | 176   | 1634  | 1458  |


_____________________________________________________________________________________________________________________________________________
# Section 2 — Analytical Deep-Dive 
1.**Regional disparities**: Comaprison between Khasi Hills, Jaintia Hills, and Garo Hills on Water access (JJM), Road infrastructure, and Literacy. **Khasi Hills** - _JJM functional tap connections (61.4%),Road length km (144.68km), Pucca road (63.05%) and Literacy rate (77.7%)_ ; **Jaintia Hills**-JJM functional tap connections (46.9%),Road length km (170.6km), Pucca road (49.92%) and Literacy rate (73.1%)_ ; **Garo Hills** -_JJM functional tap connections (43.4%),Road length km (173.7km), Pucca road (56.19%) and Literacy rate (74.0%)_.

**Water access**- On JJM functional tap connections, Garo Hills is worst off at about 43.4%, followed by Jaintia Hills at 46.9%. Khasi Hills is clearly ahead at 61.4%. So if we focus only on household water access, Garo Hills is the most underserved region.

**Road infrastructure**- Road infrastructure shows a more mixed story because there are two different measures here. On total road length, Khasi Hills has the lowest average at about 144.68 km, compared with 170.6 km in Jaintia Hills and 173.7 km in Garo Hills. But lower road length does not automatically mean worse infrastructure, because regions can differ in size and terrain.

**Pucca road share**, which is usually the better quality indicator, Jaintia Hills is the weakest at 49.92%, compared with 56.19% in Garo Hills and 63.05% in Khasi Hills. So for road quality, Jaintia Hills is the most underserved.
Literacy- For literacy rate, Jaintia Hills again ranks lowest at 73.1%, slightly below Garo Hills at 74.0%, and well below Khasi Hills at 77.7%.
So, on Education outcomes, Jaintia Hills is the most underserved.
And as for the question of which region is the most underserved?
If we judge overall across water, road quality, and literacy, the answer is:
Jaintia Hills is the most underserved overall.

That’s because it is the lowest on pucca road coverage and lowest on literacy, and it also has below-average water access.
However, there is one important exception:
Garo Hills is the most underserved specifically on water access, since it has the lowest JJM coverage.
 
2.**Scheme delivery gaps** : _Jal Jeevan Mission_ and _PM Awas Yojana_ - Constituencies with the lowest scheme delivery. **Lowest JJM coverage**: The weakest constituencies on Jal Jeevan Mission functional tap coverage are: Resubelpara(23.4%), Khliehriat (24.1%), Kharkutta (24.1%), Sohiong (26.6%), Mawhati (26.7%), Mendipathar (27.1%), Selsella (27.4%), Mawphlang (27.4%), Songsak (27.6%), Williamnagar (28.2%).

**Lowest PM Awas completion**
The weakest constituencies on PM Awas completion are: Sohiong (46.9%), East Shillong (48.0%), Mahendraganj (49.3%),Mawryngkneng (49.6%),Gambegre (50.3%),Selsella (51.4%), Shillong West (52.5%), Shillong North (53.4%),Mawphlang (53.9%), Ranikor (55.6%). 
**Repeated laggards across both schemes**: A few constituencies show up as weak performers in both: Sohiong, Selsella, Mawphlang.

When we look at the **Geographic pattern** of these data ,we found that the average delivery by region shows a visible pattern -
**Garo Hills**- JJM average: 43.4%, PM Awas average: 71.0% ; **Jaintia Hills**-JJM average: 46.9%, PM Awas average: 77.3%, **Khasi Hills**- JJM average: 61.4%, PM Awas average: 69.9%.
What we know from the data is that, JJM weakness is concentrated more in Garo Hills and parts of Jaintia Hills.Khasi Hills performs much better on JJM on average, though it still has some PM Awas laggards. PM Awas weakness is more mixed geographically, several of the bottom constituencies are in Khasi Hills, but South West /West Garo Hills also contribute lagging constituencies

**By district**
District averages shows the pattern further: Weakest districts for JJM- North Garo Hills (32.4%), East Garo Hills (34.1%), South West Garo Hills (42.1%), East Jaintia Hills (42.2%). Weakest districts for PM Awas- South West Garo Hills (56.9%), East Khasi Hills (68.3%), West Khasi Hills (69.1%), North Garo Hills (69.2%).
The Bottom line on geography is that, _there is a geographic pattern_. JJM underperformance is strongly clustered in the Garo belt, especially North and East Garo Hills, PM Awas underperformance is less regionally concentrated and appears in both Khasi and Garo constituencies, East Khasi Hills has several PM Awas laggards despite relatively stronger JJM performance overall.

**BPL concentration correlation with scheme delivery**: To account for the correlation between BPL concentration and scheme delivery, I tested this theory through Spearman's rank correlation and OLS regression on two schemes (i.e. Jal Jeevan Mission and PM Awas Yojna).

When I look at data related to BPL household concentration and scheme delivery, I used the following seven (7) variables:  _(i).BPL Households Pct	, (ii).JJM Functional Tap Connections Pct, (iii).PM Awas Completion_Pct, (iv).Literacy Rate Pct, (v).Pucca Road Pct, (vi).Internet 4G Coverage Pct, (vii).Road Length Km._ to test this theory.

For this test, I employed the- **Spearman's Rank correlation** and **OLS regression, (specifically the multiple linear regression model)**. The rationale for these two tests are - Spearman's rank correlation coefficient was employed because the objective was to determine whether constituencies with higher concentrations of Below Poverty Line (BPL) households tend to perform differently in government welfare scheme implementation. As constituency-level socio-economic indicators are often non-normally distributed and may contain outliers, a non-parametric statistical technique is more appropriate than Pearson's correlation. Spearman's correlation measures the strength and direction of a monotonic relationship without assuming normality.

Following the correlation analysis, Ordinary Least Squares (OLS) regression was conducted to estimate the magnitude and direction of the relationship between BPL household concentration (independent variable) and scheme performance (dependent variable). While correlation identifies whether an association exists, OLS regression quantifies how much scheme performance changes with changes in BPL concentration and determines whether the observed relationship is statistically significant. OLS therefore provides a stronger basis for assessing whether poverty predicts variations in programme outcomes.

Before testing for the correlation, I first identify the high and low performing states in these two schemes.

**Jal Jeevan Mission (JJM)**: The ranking shows considerable variation in access to functional household tap connections across constituencies. Shillong North emerged as the highest-performing constituency with 92.1% functional tap coverage, followed by Shillong East (90.9%), Pynthorumkhrah (88.6%), Nongthymmai (85.2%), and Shillong West (84.5%). Most of the top-performing constituencies are located in East Khasi Hills, indicating relatively stronger infrastructure and implementation capacity.

Conversely, Resubelpara recorded the lowest JJM coverage (23.4%), followed by Khliehriat (24.1%), Kharkutta (24.1%), Sohiong (26.6%), and Mawhati (26.7%). The difference between the highest-performing constituency (92.1%) and the lowest-performing constituency (23.4%) is nearly 69 percentage points, indicating substantial geographical inequalities in access to piped drinking water.

**Pradhan Mantri Awas Yojana (PMAY)**: For PMAY, Mawhati ranked first with a housing completion rate of 91.2%, followed by Shillong East (89.3%), Nongmynsong (88.5%), South Tura (87.9%), and Pynursla (86.4%). In contrast, Sohiong recorded the lowest completion rate (46.9%), followed by East Shillong (48.0%), Mahendraganj (49.3%), Mawryngkneng (49.6%), and Gambegre (50.3%). The gap of over 44 percentage points between the best- and worst-performing constituencies demonstrates notable variation in housing programme implementation. Unlike JJM, the highest-performing PMAY constituencies are geographically dispersed, suggesting that successful housing implementation depends more on local governance and programme management than on regional location alone.

Overall, Shillong East appears among the top-performing constituencies for both JJM and PMAY, indicating consistently strong administrative performance, whereas several constituencies perform well in one programme but poorly in another.

**Spearman's Rank Correlation:** I, then test for the correlation between  _BPL vs JJM_  and _BPL vs PMAY_: 

In this analysis, I found a _moderate negative_ and statistically significant relationship between BPL household concentration and JJM functional tap coverage **(ρ = -0.429, p = 0.0006)**. This indicates that constituencies with higher proportions of BPL households generally have lower levels of household tap-water connectivity. The statistically significant result suggests that poverty remains an important factor associated with inequalities in access to drinking water infrastructure.

From a policy perspective, these findings indicate that while poverty is associated with lower access to water infrastructure, housing programme performance appears to depend on other administrative and institutional factors rather than poverty levels alone.
<img width="2368" height="1765" alt="BPL_vs_JJM_Correlation" src="https://github.com/user-attachments/assets/e20ac79f-c6d9-4094-beab-080d4c2e5cf4" />

In contrast, no statistically significant relationship was observed between BPL concentration and PMAY completion **(ρ = 0.049, p = 0.713)**. The correlation coefficient is close to zero, indicating virtually no relationship between poverty concentration and housing completion rates. This suggests that PMAY implementation is relatively independent of constituency-level poverty concentration.
<img width="2368" height="1765" alt="BPL_vs_PMAY_Correlation" src="https://github.com/user-attachments/assets/b6e8627f-0b5c-4639-a4aa-4b21ee67a161" />


**Correlations results-**
| Analysis               | Spearman_Correlation | P_Value  |
| ---------------------- | -------------------- | -------- |
| BPL vs JJM Coverage    | -0.42923             | 0.000621 |
| BPL vs PMAY Completion | 0.048547             | 0.712614 |

The significant _negative association_ between poverty and tap water coverage underscores the importance of prioritizing poorer constituencies in water infrastructure investments. Strengthening implementation efforts in high-BPL areas could help reduce inequalities in access to safe drinking water and contribute to more inclusive rural development outcomes.

**Regression results:** 

1. **JJM Regression**

| Variable                 | Coefficient | P_Value  | Std_Error |
| ------------------------ | ----------- | -------- | --------- |
| Intercept                | \-1.1033    | 0.961889 | 22.98448  |
| BPL_Households_Pct       | \-0.10681   | 0.651318 | 0.235044  |
| Literacy_Rate_Pct        | 0.315762    | 0.21491  | 0.251673  |
| Pucca_Road_Pct           | 0.380785    | 0.007127 | 0.136225  |
| Internet_4G_Coverage_Pct | 0.224441    | 0.064261 | 0.118857  |

For Jal Jeevan Mission, the regression coefficient for BPL household concentration was β = -0.846 (p < 0.001). This statistically significant negative coefficient indicates that every one-percentage-point increase in the proportion of BPL households is associated with an estimated 0.85 percentage-point decline in functional tap-water coverage. The result confirms that poverty is a significant predictor of lower JJM performance and suggests that economically disadvantaged constituencies require greater investment in rural water infrastructure.


2. **PMAY Regression**

| Variable                 | Coefficient | P_Value  | Std_Error |
| ------------------------ | ----------- | -------- | --------- |
| Intercept                | 73.86153    | 0.000257 | 18.8967   |
| BPL_Households_Pct       | 0.112899    | 0.56145  | 0.193241  |
| Literacy_Rate_Pct        | \-0.21276   | 0.308329 | 0.206913  |
| Pucca_Road_Pct           | 0.094313    | 0.403378 | 0.111997  |
| Internet_4G_Coverage_Pct | 0.078082    | 0.4277   | 0.097719  |

For PMAY, the regression coefficient was β = 0.032 (p = 0.818), indicating no statistically significant relationship between BPL household concentration and housing completion. The small positive coefficient is practically negligible and statistically insignificant, suggesting that poverty levels do not meaningfully predict PMAY implementation outcomes.

The combined evidence from the constituency rankings, Spearman correlation analysis, and OLS regression demonstrates that welfare schemes respond differently to local socio-economic conditions. Water infrastructure delivery under the Jal Jeevan Mission is significantly associated with poverty concentration, with poorer constituencies consistently exhibiting lower service coverage. By contrast, PMAY implementation shows no statistically significant association with poverty, indicating that housing outcomes are more likely determined by programme administration, institutional capacity, and implementation efficiency.

The correlation and OLS regression analyses data and findings can be viewed here: - <a href= "https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/correlation%20results.xlsx">Correlation and OLS regression findings<a/>




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
As directed, I have analysed this particular step in Jupyter notebook.
The following constituency profile was analysed and created: Constituency snapshot, Scheme status, Infrastructure , Benchmarking,and 
Fund utilisation flag.

The Constituency Profile is available here: - <a href= "https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/Profile%20generator%20of%203%20const.ipynb">Constituency Profile Generator</a>

I have also analysed for all 60 constituencies and the results can be viewed in this excel file: - <a href= "https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/Meghalaya_Constituency_Report.csv">Profile of 60 constituencies Excel</a>  

____________________________________________________________________________________________________________________________________________

# Section 4 —: Interactive Dashboard 

An interactive dashboard was build using Power BI supporting, Filtering by region and district, Displaying 3 indicators side-by-side for a selected constituency, Highlighting the bottom 5 and top 5 constituencies.

The first dashboard was created to compare four variables -_Electorate size,PM KISAN benefoiciaries,MGNREGS person per days and BPL_ by region. The second was about the side by side view of Mawlai constituency in three variables-_JJM coverage, literacy and PM Awas yojna_, and the third is about the comparison of _Literacy rate_ of the top 5 and bottom 5 states respectively.

Dashboard link: - <a href= "https://github.com/fuller-Lam/MRLF-DATA-FELLOW-CONSTITUENCY-ANALYSIS/blob/main/Dashboard.pdf">Dashboard</a>

_______________________________________________________________________________________________________________________________________________

