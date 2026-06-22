## 📚 Table of Contents

1. [Project objectiv](#-Project-objective)
2. [Executive Summary](#Executive--Summary)
3. [Methodology & Data Cleaning](#Methodology-data--cleaning)  
4. [Key Findings & Insights](#Key-Findings-&--Insights) 
6. [Dashboard](#-dashboard)  
7. [Recomendations](#Recomendations)  
8.  [About Me](#-about-me)

# [Project objective](#-Project-objective)

Project Objective
Deliver a clear, insight‑focused analysis of Panama’s economic landscape, highlighting the sectors and regions that offer the highest potential for Dajcom’s home appliances, food, and beverage portfolio.

📊 Key Analysis Areas
1. Overall Economic Growth
Evaluate Panama’s annual and quarterly GDP trends.

Assess economic stability and growth momentum.

Identify the optimal timing and scale for market entry.

2. Sector Performance
Analyze GDP contribution and growth across major industries.

Focus on food, beverages, manufacturing, logistics, and retail.

Highlight sectors with consistent growth and strong demand signals.

3. Foreign Direct Investment (FDI)
Review FDI inflows by sector over the last 5–10 years.

Identify industries attracting international capital.

Assess policy, infrastructure, and investment incentives.

4. Key Economic Indicators
National & provincial GDP growth

Sectoral contribution to GDP

CAGR for priority sectors

FDI growth and concentration patterns

These indicators help compare opportunities and rank the most promising sectors.

5. Regional & Provincial Insights
Provincial GDP and economic activity

Infrastructure strength (ports, highways, free zones)

Labor availability and urbanization

Market access and distribution potential

This supports location decisions for manufacturing, warehousing, and distribution.

🧭 Strategic Deliverables
Market insights dashboard (GDP, sectors, FDI, regions)

Sector opportunity ranking

Province selection matrix (infrastructure, labor, access)

Risk assessment + mitigation plan

Entry strategy roadmap (short, medium, long term)

✅ Expected Outcome
A concise, data‑backed view of Panama’s economic environment that enables Dajcom leadership to:

Prioritize high‑potential sectors

Select the best regions for operations

Reduce investment risk

Build a focused, scalable market entry strategy

 # [Methodology & Data Cleaning](#Methodology-data--cleaning)
## Panama Macroeconomic Data Cleaning Documentation
A Multi‑Dataset ETL Pipeline for FDI, GDP, GVA & Provincial Indicators (2017–2023)
- Tools:  Power BI, SQL, Excel
- Data Sources: INEC Panama (FDI, GDP, GVA, Provincial GDP, Quarterly GDP)
## Project Overview
This project consolidates and cleans multiple macroeconomic datasets from INEC Panama to build a unified analytical foundation for studying.
Foreign Direct Investment (FDI)
Gross Value Added (GVA)
Annual GDP
Provincial GDP
Quarterly GDP
Sector‑level economic performance

## Standardized Data Cleaning Framework
All datasets were processed using the same senior‑level ETL methodology:

### Ingestion
Imported Excel/CSV files using SQL and Power BI.

Inspected raw structure to identify metadata, merged cells, footnotes, and non‑data rows.

### Structural Cleaning
Removed metadata rows, titles, footnotes, and totals.
Example from the document:

- Removed irrelevant rows (1–9, 11, 30–34) that contained notes or were entirely empty.

- Promoted the correct header row.

- Renamed key identifier columns (e.g., Descripción → Sector, País de origen → Country).

### Standardization
- Trimmed whitespace, corrected spelling inconsistencies, and harmonized sector/country names.

- Ensured consistent naming across datasets (e.g., “Sector”, “Year”, “GDP_Value”).

### Reshaping
- Unpivoted all year columns into long format to support time‑series analysis.
- Example from the document:

-Unpivoted the dataset from wide to long format for easier analysis.

### Data Type Validation
- Converted Year → integer

- Converted GDP/FDI/GVA values → float

- leaned thousands separators and decimal inconsistencies.

### Deduplication & Integrity Checks
Verified unique primary keys (Sector‑Year, Country‑Year, Province‑Year).

Removed totals, subtotals, and alias rows.

### Export
Saved each cleaned dataset as a separate CSV file with standardized naming conventions.

# Dataset‑Specific Cleaning Documentation
### FDI by Economic Activity (2017–2023)
File: FDI_Economic_Activity_2017_2023.csv  
Rows: 119
Columns: Economic Sector, Year, FDI_Value

**Key Cleaning Actions**
- Removed metadata rows and explanatory notes.

- Renamed first column to Economic Sector.

- Excluded provisional/inconsistent values (2020–2023).

- Removed participation % and YoY variation columns.

- Filled down merged sector names.

- Unpivoted 2017–2023 columns.

 **Document citation:**

I removed the last two columns—participation percentage and year-over-year variation—since they weren't needed.

### FDI by Country of Origin (Top 10, 2017–2023)
File: FDI_Country_Origin_2017_2023.csv  
Rows: 70
Columns: Country, Year, FDI_Value

**Key Cleaning Actions**
- Removed metadata rows and empty rows.

- Dropped participation % and variation % columns.

- Removed national totals and “Otros países”.

- Standardized country names.

- Unpivoted year columns.

- Document citation:

- Excluded 'Otros países': Limited scope to only the top 10 countries

### Gross Value Added (GVA) by Sector (2018–2022)
File: GVA_Sector_2018_2022.csv  
Rows: 95
Columns: Sector, Year, GVA_Value

**Key Cleaning Actions**
- Removed metadata and non‑data rows.

- Promoted correct headers.

- Standardized sector names.

- Removed subtotals and totals.

- Unpivoted year columns.

- Document citation:

- Removed subtotal and total rows… retaining only granular, sector-level data points.

### GDP by Economic Activity (1996–2022)
File: GDP_Economic_Activity_1996_2022.csv  
Rows: 433
Columns: Sector, Year, GDP_Value

**Key Cleaning Actions**
- Removed metadata and footnotes.

- Dropped non‑data rows at top and bottom.

- Standardized sector descriptions.

- Unpivoted 1996–2022 columns.

- Validated numeric formats.

- Document citation:

- Removed Column 1 containing metadata and notes irrelevant to analysis.

### Annual GDP (2018–2023)
File: GDP_Annual_2018_2023.csv  
Rows: 139
Columns: Sector, Year, GDP_Value

**Key Cleaning Actions**
- Removed titles, footnotes, and totals.

- Standardized sector names.

- Unpivoted year columns.

- Cleaned numeric formatting.

- Document citation

Removed aggregated total rows and checked for duplicate sector-year entries.

### Provincial GDP (2018–2023)
File: GDP_Provincial_2018_2023.csv  
Rows: 60
Columns: Province, Year, P_GDP_Value

**Key Cleaning Actions**
- Removed national-level categories.

- Standardized province names.

- Unpivoted year columns.

- Removed duplicates and totals.

- Document citation

- Filtered sector rows… to focus only on GDP by province.

### Quarterly GDP (2018–2023)
File: GDP_Quarterly_2018_2023.csv  
Rows: 486
Columns: Sector, Quarter, Q_GDP_Value

**Key Cleaning Actions**
- Removed metadata and footnotes.

- Removed national totals (e.g., Valor Agregado Bruto).

- Standardized sector names.

- Unpivoted quarter columns.

- Cleaned numeric formatting.
  ![Relationship](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/blob/main/MODEL%20RELATIONSHIP.png)



# [Key Finding & Insights](#Key-Findings-&--Insights)

## Panama’s Economic Growth: A Market Moving in the Right Direction
The dashboard shows a clear recovery and steady expansion.
After the sharp drop in 2020, annual GDP climbed from $47.5K to $67.9K by 2023. Growth moved from –20% to +18%, +12%, and +8% in three consecutive years.

Quarterly GDP moves up and down, but the average stays around $17K, which signals a stable base of economic activity.

**Insight:**  
Panama is not just recovering - it is growing with consistency, creating a safe window for Dajcom to enter within the next 1–3 years.


## Sector Performance: Where Panama’s Growth Is Coming From
The sector dashboards highlight the engines of the economy.
Between 2018–2022, the strongest contributors are:

Commerce

Transport & logistics

Construction

Utilities

Service activities

Long‑term trends (1996–2022) show fast growth in:

Exploitation (16% CAGR)

Construction (11% CAGR)

Utilities (9% CAGR)

Transport (7% CAGR)

These sectors match Dajcom’s product lines and operating model.
- Construction growth supports home appliance demand.
- Commerce growth supports food and beverage distribution.
- Transport growth supports logistics and warehousing.

**Insight:**  
Panama’s sector mix aligns well with Dajcom’s strengths, especially in retail, logistics, and consumer goods.

![Sectoral Performance](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/blob/main/SECTORAL%20PERFORMANCE.png)
![Key sector](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/blob/main/KEY%20SECTOR.png)

## Foreign Direct Investment: Strong Confidence From Global Companies
FDI is one of the clearest signals in the dashboard.

$403M total FDI (2017–2023)

~500% CAGR

Growth stabilizing around 35–36%

This shows that global companies are not only entering Panama — they are expanding their investments across logistics, construction, and services.

**Insight:**  
High FDI confirms that Panama offers a business‑friendly environment, strong infrastructure, and predictable rules.
This reduces risk for Dajcom and supports long‑term planning.

![FDI](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/blob/main/FDI%20GDP.png)

## Regional & Provincial Insights: Where Economic Activity Is Concentrated
The provincial analysis shows that most economic activity is concentrated in four regions:

Panamá - main economic center

Colón - logistics and Free Trade Zone

Panamá Oeste - fast‑growing industrial and residential area

Chiriquí - rising commercial and agricultural hub

Together, these regions account for almost 90% of national GDP.

Partner‑country data shows strong ties with:

- United States

- Colombia

- Canada

- Europe

This reinforces Panama’s position as a global trade hub.

**Insight:**  
Dajcom should anchor operations in Panamá city and Panamá Oeste, use Colón for import/export, and consider Chiriquí for future manufacturing or regional distribution.

![Provincial](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/blob/main/PROVINCE%20AND%20TOP%20COUNTRIES.png)

### Key Indicators: What the Numbers Say About Market Potential
Across the dashboards, the indicators point in the same direction:

GDP CAGR (2018–2022): 3%

Sector CAGR (1996–2022): 6%

FDI CAGR (2017–2023): 500%

Total GVA (2018–2022): $324K

These numbers show a healthy, expanding economy with strong sector performance and rising investment.

**Insight:**  
Panama’s growth is broad‑based, not dependent on one sector.
This creates a stable environment for long‑term investment and expansion.

Dashboard pages used:

Annual & Quarterly GDP

Key Sector Contributing to GDP

Sectoral Performance Trends

FDI GDP

# [Dashboard](#-dashboard)
![Click here](<iframe title="power bi panama growth analysis" width="600" height="373.5" src="https://app.powerbi.com/view?r=eyJrIjoiZWM5MjIxOGQtNGQ0Yi00MzEyLWI1YjEtNzU3ZjgxZTJjYzk4IiwidCI6IjVmNTY2NGU1LWYzNjktNDliYi1hZjRjLWU0YTVkMmRmNTRhNyIsImMiOjJ9" frameborder="0" allowFullScreen="true"></iframe>)



 # [Recomendations](#Recomendations)
### Enter the market in phases
Start with import and distribution in Panamá and Panamá Oeste.

Build a regional distribution hub in Colón or Panamá Oeste.

Explore local manufacturing once demand scales.

### Focus on high‑opportunity sectors
- Food & beverage

- Home appliances

- Retail and commerce

- Logistics partnerships

### Choose locations that match your strategy
- Panamá City - Corporate and sales

- Panamá Oeste - Warehousing

- Colón - Import/export

- Chiriquí  Future manufacturing

### Manage risks early
Use flexible inventory to handle quarterly GDP swings.

Balance exposure across retail, logistics, and manufacturing.

Maintain strong local advisory support for regulations.
	
# [About Me](#-about-me)
 Data Analyst with experience in sales, customer service, inventory management, and logistics operations. Specialized in the use of SQL, Excel, and Power BI to analyze data,reports, and create visualizations that support data‑driven decision‑making.

I am currently developing inventory, logistics, and supply chain analytics projects to strengthen my skills in business intelligence and process optimization.

Tools: SQL, Power BI, Excel, Python.


