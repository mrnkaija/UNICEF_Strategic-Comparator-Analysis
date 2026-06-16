# UNICEF: Strategic Comparator Analysis (SCA)

**Objective**: 

Develop an end-to-end Business Intelligence (BI) pipeline that
1. ingests multi-INGO income data
2. automates SCA file generation per IFL protocols
3. builds interactive Power BI reports for global/regional/market-level insights
4. enables scenario modeling (e.g., PSFR funding cuts)
5. benchmarks costs/donor efficiency

**Key pipeline production features:**
1.	Scalability: can be scaled from 100K to 1M+ records using SQL
2.	Automation: Can be run automatically every Monday without manual refresh and visible to all Country Representatives/Directors
3.	Security: Row Level Security (RLS) prepared: Kenya Director sees Kenya gaps; Switzerland Director sees Switzerland gaps. Single secure dashboard
4.	Mobile: Responsive executive design
5.	Validated format: CSV outputs validated for International Fundraising Leadership Forum (IFL) data analytics vendor (Adroit)

**Methodology**:
I use Python to generate a realistic synthetic 55-market dataset with 100k records modeling 16 INGOs (UNICEF + peers like SaveTheChildren, Oxfam) across 55 markets, 2024-2025 income by channel (PSFR, Digital, Corporate), growth rates, costs


**Executive Summary:**
This is a one-month end to end solution that processes 100K fundraising records across 55 markets and 7 NGOs generating Adroit-ready gap analysis and a 4-page Power BI executive dashboard. The synthetically generated data includes the following NGOs:
1.	UNICEF
2.	Save The Children
3.	Oxfam
4.	RedCross
5.	World Vision
6.	Plan International
7.	CARE


**Technical Architecture:**
**1.	Data Generation:** 
I used Python (generate_data.ipynb) to generate 100K synthetic records covering 55 Markets, 7 NGOs and 5 income channels. Output was a 13MB Microsoft Excel File (sca_prototype.xlsx)

 **2.	Extract, Transform, and Load (ETL):**
 a.	Using Microsoft Excel, I cleaned/formatted the data and created Pivot Tables and Slicers to test the viability of the generated dataset
 b.	I then used Python to generate a pipeline of vendor-ready (Adroit) files that include:
        •	sca.db (SLQ intermediate store ready)
        •	sca_output.csv
        •	unicef_scenarios.csv
        •	powerbi_summary.csv
  

**3.	Visualization:** 
I then used the generated files for Power BI Relationships to generate visualizations in the final file sca_dashboard.pbix with four (4) interactive pages
 
**Dashboard Pages:**
**Page 1: Executive Overview**
•	4 KPI Cards: UNICEF Share, Gap Total, PSFR Growth and Crisis Impact
•	Regional Column Chart: UNICEF vs Peers
•	Table: Market, UNICEF Income, Channel, Gap
•	Market Map: Gap saturation
 
**Page 2: Market Drilldown**
•	Matrix: Market, UNICEF Income, Gap
•	Slicers: Region, Channel
 
**Page 3: Efficiency/Risk Analysis**
•	Scatter: Cost per donor (X-Axis) Vs. Growth Rate (Y-Axis)
•	Table: Cost per donor, Growth rate
•	Slicers: Region, Channel
 

**Page 4: Channel Performance**
•	Stacked Column: Channel mix by Region
•	Gauge: PSFR Growth (Target 15%)
•	KPI: Total Gap trend
 
**Key Findings and Recommendations:**
1.	Key Finding: Switzerland PSFR: +USD 3.3K gap vs peers
2.	Recommendations:
a.	Reallocate 10% Europe PSFR budget to identified high growth markets
b.	Scale Switzerland PSFR model regionally
c.	Optimize Cost Per Donor to less than $50 across markets
