

# Strategic-Market-Entry-Assessment-Panama
### A data-driven project designed to evaluate Panama’s economic landscape and identify key sectors, regions, and investment trends for successful business entry. Using tools like Power BI, Excel, and DAX, the analysis focuses on GDP performance, foreign direct investment, and sectoral growth to guide informed market entry decisions

## 📚 Table of Contents

1. [About Me](#-about-me)  
2. [Business Request](#-business-request)
3. [Executive Summary](#Executive--Summary)  
4. [Methodology & Data Cleaning](#Methodology-data--cleaning)  
5. [Key Finding & Insights](#Key-Findings-&--Insights) 
6. [Dashboard](#-dashboard)  
7. [🧠 DAX Modelling & Relationships](#-dax-modelling--relationships)  
8. [🗂️ Data Sources](#-data-sources)

#  [Executive Summary](#Executive--Summary) 

## Why Panama Matters
Panama is a small country with a big economic engine. Over the last few years, the economy has shown strong recovery, steady growth, and a clear shift toward logistics, commerce, and services. For a company like Dajcom — operating in home appliances, food, and beverages — Panama offers a mix of market demand, logistics strength, and investment‑friendly conditions.

The dashboards you provided help us see this story clearly.

# [👤 About Me](#-about-me)
Data Analyst with experience in sales, customer service, inventory management, and logistics operations. Specialized in the use of SQL, Excel, and Power BI to analyze data,reports, and create visualizations that support data‑driven decision‑making.

I am currently developing inventory, logistics, and supply chain analytics projects to strengthen my skills in business intelligence and process optimization.

Tools: SQL, Power BI, Excel, Python.

# [Business Request](#-business-request)
### project overview
We are Dajcom Limited, a leading company in the home appliances, food, and beverage industry. As we explore strategic opportunities to expand our operations into Panama, we are seeking your expertise to support us with a market analysis that will guide our investment and entry decisions.

Project Objective
The goal of this project is to provide a clear and data-informed overview of Panama’s economic environment, focusing on the following key areas:
1.	Overall Economic Growth
o	What we need: Insights into Panama’s economic performance based on annual and quarterly GDP trends.
o	 This will help us understand the stability and future potential of the market, so we can determine the right time and scale for entering Panama.
2.	Sector Performance
o	What we need: Analysis of which industries contribute most to Panama’s economy, especially those growing steadily. We are particularly interested in sectors related to food, beverages, manufacturing, logistics, and retail.
o	Why it matters: This will help us identify which sectors to focus on or partner with for sourcing, production, or distribution.
3.	Foreign Direct Investment (FDI)
o	What we need: An overview of FDI trends by sector, to see where international companies are choosing to invest.
o	Why it matters: Sectors that attract FDI usually have favorable policies, infrastructure, and growth potential. This will give us confidence about where to align our investment strategy.
4.	Key Economic Indicators
o	What we need: A summary of key figures, such as:
	GDP growth (national and provincial)
	Sectoral contribution to GDP
	Compound Annual Growth Rate (CAGR)
	FDI growth by sector
o	Why it matters: These figures will help us compare opportunities and select the best sectors and regions for investment.
5.	Regional and Provincial Insights
o	What we need: Analysis of economic GDP activity at the provincial level, highlighting infrastructure, market access, labor availability, and urbanization.
o	Why it matters: This will help us choose the right locations for operations such as manufacturing, warehousing, or distribution.
6.	Strategic Recommendations
o	What we need: A clear summary of opportunities and risks, along with suggested sectors and regions to prioritize.
o	Why it matters: Your guidance will help ensure our market entry strategy is focused, data-backed, and aligned with Panama’s economic landscape.
Expected Deliverable
We are looking for a well-structured report that includes data visualizations (such as charts or dashboards) to clearly present insights. The report should include practical takeaways we can use to inform leadership decisions.
________________________________________

 # [🧹 Data Cleaning](#-data-cleaning) 
## Panama Macroeconomic Data Cleaning Documentation
A Multi‑Dataset ETL Pipeline for FDI, GDP, GVA & Provincial Indicators (2017–2023)
Tools:  Power BI, SQL, Excel
Sources: INEC Panama (FDI, GDP, GVA, Provincial GDP, Quarterly GDP)
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
Imported Excel/CSV files using Python and Power BI.

Inspected raw structure to identify metadata, merged cells, footnotes, and non‑data rows.

### Structural Cleaning
Removed metadata rows, titles, footnotes, and totals.
Example from the document:

“Removed irrelevant rows (1–9, 11, 30–34) that contained notes or were entirely empty.”

Promoted the correct header row.

Renamed key identifier columns (e.g., Descripción → Sector, País de origen → Country).

### Standardization
Trimmed whitespace, corrected spelling inconsistencies, and harmonized sector/country names.

Ensured consistent naming across datasets (e.g., “Sector”, “Year”, “GDP_Value”).

### Reshaping
Unpivoted all year columns into long format to support time‑series analysis.
Example from the document:

“Unpivoted the dataset from wide to long format for easier analysis.”

### Data Type Validation
Converted Year → integer

Converted GDP/FDI/GVA values → float

Cleaned thousands separators and decimal inconsistencies.

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

Key Cleaning Actions
Removed metadata rows and explanatory notes.

Renamed first column to Economic Sector.

Excluded provisional/inconsistent values (2020–2023).

Removed participation % and YoY variation columns.

Filled down merged sector names.

Unpivoted 2017–2023 columns.

Document citation:

"I removed the last two columns—participation percentage and year-over-year variation—since they weren't needed…”

### FDI by Country of Origin (Top 10, 2017–2023)
File: FDI_Country_Origin_2017_2023.csv  
Rows: 70
Columns: Country, Year, FDI_Value

Key Cleaning Actions
Removed metadata rows and empty rows.

Dropped participation % and variation % columns.

Removed national totals and “Otros países”.

Standardized country names.

Unpivoted year columns.

Document citation:

“Excluded 'Otros países': Limited scope to only the top 10 countries…”

### Gross Value Added (GVA) by Sector (2018–2022)
File: GVA_Sector_2018_2022.csv  
Rows: 95
Columns: Sector, Year, GVA_Value

Key Cleaning Actions
Removed metadata and non‑data rows.

Promoted correct headers.

Standardized sector names.

Removed subtotals and totals.

Unpivoted year columns.

Document citation:

“Removed subtotal and total rows… retaining only granular, sector-level data points.”

### GDP by Economic Activity (1996–2022)
File: GDP_Economic_Activity_1996_2022.csv  
Rows: 433
Columns: Sector, Year, GDP_Value

Key Cleaning Actions
Removed metadata and footnotes.

Dropped non‑data rows at top and bottom.

Standardized sector descriptions.

Unpivoted 1996–2022 columns.

Validated numeric formats.

Document citation:

“Removed Column 1 containing metadata and notes irrelevant to analysis…”

### Annual GDP (2018–2023)
File: GDP_Annual_2018_2023.csv  
Rows: 139
Columns: Sector, Year, GDP_Value

Key Cleaning Actions
Removed titles, footnotes, and totals.

Standardized sector names.

Unpivoted year columns.

Cleaned numeric formatting.

Document citation:

“Removed aggregated total rows and checked for duplicate sector-year entries.”

### Provincial GDP (2018–2023)
File: GDP_Provincial_2018_2023.csv  
Rows: 60
Columns: Province, Year, P_GDP_Value

Key Cleaning Actions
Removed national-level categories.

Standardized province names.

Unpivoted year columns.

Removed duplicates and totals.

Document citation:

“Filtered sector rows… to focus only on GDP by province.”

### Quarterly GDP (2018–2023)
File: GDP_Quarterly_2018_2023.csv  
Rows: 486
Columns: Sector, Quarter, Q_GDP_Value

Key Cleaning Actions
Removed metadata and footnotes.

Removed national totals (e.g., Valor Agregado Bruto).

Standardized sector names.

Unpivoted quarter columns.

Cleaned numeric formatting.



# [📊 Presentation & Recommendations](#presentation--recommendations)  

![Captura de pantalla 2025-06-17 213252](https://github.com/user-attachments/assets/c59016eb-0edc-42d8-aa64-87f1a2c34318)

[![Slide Preview](./slide-preview.png)](./powerpoint%20data%20presentation.pptx)
🔗 [Click here to download the full PowerPoint presentation](./powerpoint%20data%20presentation.pptx)

# [📈 Dashboard](#-dashboard)
[📈 View Dashboard](<iframe title="power bi panama growth analysis" width="600" height="373.5" src="https://app.powerbi.com/view?r=eyJrIjoiZWM5MjIxOGQtNGQ0Yi00MzEyLWI1YjEtNzU3ZjgxZTJjYzk4IiwidCI6IjVmNTY2NGU1LWYzNjktNDliYi1hZjRjLWU0YTVkMmRmNTRhNyIsImMiOjJ9" frameborder="0" allowFullScreen="true"></iframe>)

)

 # [🧠 DAX Modelling & Relationships](#-dax-modelling--relationships)

### BridgeTableYear 
Purpose: Creates a consistent year table from 1996 to 2025 to link with all time-based fact tables.
•	Ensures uniform year values
•	Supports clean one-to-many relationships
•	Improves filtering, DAX accuracy, and report performance

Code = let
    StartYear = 1996,
    EndYear = 2025,
    YearList = List.Generate(
        () => StartYear,
        each _ <= EndYear,
        each _ + 1
    ),
    YearTable = Table.FromList(YearList, Splitter.SplitByNothing(), {"Year"})
in
    YearTable

### QuarterTable 
Purpose: Generates combinations of Year and Quarter (e.g., 2018Q1) from 2018 to 2025.
•	Enables seasonal analysis
•	Links cleanly to quarterly GDP 
•	Avoids redundant year/quarter logic in reports

Code = let
    StartYear = 2018,
    EndYear = 2025,
    Quarters = { "Q1", "Q2", "Q3", "Q4" },
    YearQuarterList = List.Combine(
        List.Transform(
            {StartYear..EndYear},
            each List.Transform(Quarters, (q) => Text.From(_) & q)
        )
    ),
    YearQuarterTable = Table.FromList(YearQuarterList, Splitter.SplitByNothing(), {"YearQuarter"})
in
    YearQuarterTable
 ### DimSector 
Purpose: Combines and cleans Sector columns from multiple fact tables to create a unified dimension.
•	Resolves many-to-many issues with a one-to-many model
•	Standardizes naming (trimming, casing)
•	Enables consistent filtering and accurate DAX

Code = let
    // Select and rename Sector columns for consistency
    GDP_Annual = Table.RenameColumns(Table.SelectColumns(#"Panama’s_Annual_GDP__2018_2023", {"Sector"}), {{"Sector", "Sector"}}),
    GDP_Quarterly = Table.RenameColumns(Table.SelectColumns(#"Panama’s_Quarterly_GDP__2018_2023", {"Sector"}), {{"Sector", "Sector"}}),
    FDI = Table.RenameColumns(Table.SelectColumns(#"FDI__by_Economic_Activity", {"Sector"}), {{"Sector", "Sector"}}),
    GVA = Table.RenameColumns(Table.SelectColumns(#"Gross_Value_Added__GVA__by_Economic_Sector", {"Sector"}), {{"Sector", "Sector"}}),
    GDP_Historical = Table.RenameColumns(Table.SelectColumns(#"Panama’s GDP by Economic Activities", {"Sector"}), {{"Sector", "Sector"}}),

    // Combine all sectors
    AllSectors = Table.Combine({GDP_Annual, GDP_Quarterly, FDI, GVA, GDP_Historical}),

    // Clean: Trim whitespace, remove nulls/empty, and lowercase for standardization
    CleanedSectors = Table.SelectRows(AllSectors, each [Sector] <> null and Text.Trim([Sector]) <> ""),
    TrimmedSectors = Table.TransformColumns(CleanedSectors, {{"Sector", Text.Trim}}),
    LowerCased = Table.TransformColumns(TrimmedSectors, {{"Sector", Text.Lower}}),

    // Remove duplicates
    UniqueSectors = Table.Distinct(LowerCased),

    // Capitalize sector names again (optional)
    Capitalized = Table.TransformColumns(UniqueSectors, {{"Sector", Text.Proper}}),

    // Add SectorKey
    AddKey = Table.AddIndexColumn(Capitalized, "SectorKey", 1, 1, Int64.Type)
in
    AddKey
    [Click here for full detail](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/raw/refs/heads/main/DAX%20CODES.docx)

    
![Captura de pantalla 2025-06-14 192436](https://github.com/user-attachments/assets/44995f4f-5053-48e9-a22b-0a0e1337d3f2)
![Captura de pantalla 2025-06-14 192750](https://github.com/user-attachments/assets/2d18b783-f847-484e-83fb-5cf873532574)
# [🗂️ Data Sources](#-data-sources) 
 1. Panama’s GDP by Economic Sector
•	Source: INEC Panama – National Accounts by Sector :( CUENTAS ESPECIALES-
Serie Homogénea 1996-2022, con año de referencia 2018	•	
1996-2022)
•	Purpose: Tracks the annual GDP contribution by each sector.
•	Columns:
o	Sector: Name of the economic sector
o	Year: Reporting year
o	GDP: GDP value (likely in million USD or Balboas)

 [Click here for full detail](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/raw/refs/heads/main/tables%20doccumentaion.docx)


