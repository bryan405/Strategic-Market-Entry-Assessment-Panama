

# Strategic-Market-Entry-Assessment-Panama

## 📚 Table of Contents

1. [👤 About Me](#-about-me)  
2. [💼 Business Request](#-business-request)  
3. [🧹 Data Cleaning](#-data-cleaning)  
4. [📊 Presentation](#-presentation)  
5. [📈 Dashboard](#-dashboard)  
6. [🧠 DAX Modelling & Relationships](#-dax-modelling--relationships)  
7. [🗂️ Data Sources](#-data-sources)  

### [👤 About Me](#-about-me)
From selling electronics on the buzzing streets of Nigeria to managing mouthwatering empanadas in Panama —and now uncovering insights through data—I’ve had quite the journey!
I’m a versatile professional with over 7 years of experience in sales, hands-on leadership in food production and marketing, and an academic background in Biology, Biotechnology (B.Sc.), and Food Safety (M.Sc.). My passion for problem-solving, systems thinking, and business strategy naturally led me to the world of data analytics.
Now, I'm helping businesses make smarter decisions through data. I turn messy datasets into actionable insights, build dashboards that actually tell stories, and use analytics to solve real-world problems—especially in sales, marketing, and food safety domains.
Tools I work with:
Power BI | Excel | SQL | Python | DAX | Data Storytelling
 What I care about:
•	Helping small businesses grow using data
•	Making food systems safer and smarter
•	Creating visuals that speak louder than slides
•	Continuous learning and community impact
 Currently building projects across sales, food safety, and economic trends in Panama.
Let’s connect if you're into data, food, strategy—or just curious how an empanada guy became a data guy!
### project overview
We are Dajcom Limited, a leading company in the home appliances, food, and beverage industry. As we explore strategic opportunities to expand our operations into Panama, we are seeking your expertise to support us with a market analysis that will guide our investment and entry decisions.
### Project Objective
The goal of this project is to provide a clear and data-informed overview of Panama’s economic environment, focusing on the following key areas:
1.	Overall Economic Growth
	What we need: Insights into Panama’s economic performance based on annual and quarterly GDP trends.
	 This will help us understand the stability and future potential of the market, so we can determine the right time and scale for entering Panama.
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
   # [🧹 Data Cleaning & Transformation](#-data-cleaning--transformation)
   ### Dataset no:1
Data Cleaning & Documentation – FDI by Economic Activity (Panama, 2017–2023)
Source: INEC Panama – Table 7
Topic: Foreign Direct Investment (IED) by Economic Activity
Unit: Thousands of Balboas (B/.)
Coverage: Annual data, 2017 to 2023 (as of December 31 each year)
Format: Excel
Primary Key: Combination of Economic Sector and Year
________________________________________
🔍 Raw Data Overview
The dataset includes FDI values by economic sector along with sector participation and year-over-year variation for 2023.

Data Cleaning Summary – FDI by Economic Activity (Panama)
To prepare the dataset for analysis, I first removed irrelevant rows (1–9, 11, 30–34) that contained notes or were entirely empty. I promoted the correct header row, which included the years 2017–2023, to use as column names.
I renamed the first column to "Economic Sector" for clarity, then filtered out rows containing non-data text like explanatory notes and footnotes (e.g., rows 19–21). I also excluded data from 2020 to 2023 that appeared inconsistent or labeled as provisional.
Next, I removed the last two columns—participation percentage and year-over-year variation—since they weren't needed for our core analysis and could be recalculated later if needed.
I checked for and confirmed there were no duplicate rows. Then I used fill down to complete any missing sector names, corrected the data types (ensuring years were numeric and FDI values were in number format), and unpivoted the dataset from wide to long format for easier analysis.
Finally, I renamed the columns to:
•	Economic Sector
•	Year
•	FDI Economic value
The cleaned dataset now has 119 rows and 3 columns.
Cleaned file name: FDI by Economic Activity (Panama, 2017–2023)

### Data Source 2: 
Foreign Direct Investment (FDI) by Country of Origin – Panama (2017–2023)
•	Source: INEC Panama – Table 2
•	Topic: FDI Position by Country of Origin (Top 10)
•	Unit: Thousands of Balboas (B/.)
•	Period Covered: 2017 to 2023 (as of December 31)
•	Format: Excel
•	Primary Key: Composite — Country + Year
________________________________________
🧹 Data Cleaning Summary
1.	Removed irrelevant rows and notes: Rows 1–8, 10, and 24–28 contained metadata, footnotes, or were completely empty — not needed for analysis.
2.	Promoted header row: Used the row containing year labels (2017–2023) as column headers to enable structured time-series analysis.
3.	Dropped percentage columns: Columns 9 and 10 (participation %, variation %) were removed — can be recalculated dynamically when required.
4.	Deleted extra empty columns: Columns 11 and 12 had no data and were dropped for a cleaner scheme.
5.	Removed total FDI rows: National-level totals were excluded, as we’re focusing on country-level breakdowns and can compute totals separately.
6.	Excluded 'Otros países': Limited scope to only the top 10 countries for focused analysis.
7.	Checked for duplicates: Ensured no duplicate entries for the same country-year combination.
8.	Applied fill-down: Filled missing country names in merged cells for consistency.
9.	Validated data types: Ensured country = text, year = integer, value = numeric.
10.	Renamed ‘País de origen’ to ‘Country’: Aligned with English-language reporting standards.
11.	Corrected spelling inconsistencies: Standardized country,year names for consistency across the table.
12.	Unpivoted yearly columns: Transformed the table from wide to long format — one row per country-year entry — to support easy analysis.
13.	Renamed columns for clarity: Renamed unpivoted fields as Year and FDI_Value.
________________________________________
✅ Cleaned Dataset Overview
•	Final Columns: 3 — Country, Year, FDI_Value
•	Total Rows: 70 (10 countries × 7 years)
•	Cleaned file name: FDI Position by Country of Origin (Top 10)
### Data Source 3
Dataset Summary: Gross Value Added (GVA) by Economic Sector – Panama (2018–2022)
Source: INEC Panama
Topic: Sector-wise Gross Value Added (Valor Agregado Bruto) at basic prices
Reference Year: 2018 (for price adjustments)
Format: Excel (Table 2)
Years Covered: 2018 to 2022
Data Cleaning Summary: Gross Value Added (GVA) by Economic Sector
1.	Removed metadata and notes from column 1 and eliminated the first 6 rows and the last 13 rows from columns 2 to 7 due to nulls and non-data text.
2.	Dropped non-data rows (e.g. rows 6, 9, 14, and 23) used for category labels or totals to retain only usable records.
3.	Promoted proper headers, aligning column names with sector names and year values for clarity.
4.	Renamed column 1 sector- category to Sector for clear identification of economic activities.
5.	Unpivoted year columns into long format (Sector, Year, GVA_Value) to make the data analysis ready.
6.	Standardized sector names and corrected spelling inconsistencies year and across the sector column to ensure uniform labeling across all records.
7.	Validated data types: confirmed that Year is numeric and GVA_Value is a float; also reviewed for alias values and corrected them.
8.	Checked for and removed duplicates based on unique Sector-Year pairs.
9.	Removed subtotal and total rows, in row 26 to 29 retaining only granular, sector-level data points for accurate analysis.
________________________________________
✅ Final Dataset Structure:
•	Columns: 3 — Sector, Year, GVA_Value
•	Rows: 95
•	Cleaned File Name: Gross Value Added (GVA) by Economic Sector
•	to Identify Sectoral Growth Drivers and Investment Opportunities (2018–2022)


### Data source 4
Data Cleaning Summary: Panama’s GDP by Economic Activity (1996–2022)
Source: INEC Panama – Cuadro 1
Topic: GDP at Purchaser Prices by Economic Activity
Unit: Millions of Balboas (B/.)
Period: 1996–2022
________________________________________
Cleaning Actions:
•	Removed Column 1 containing metadata and notes irrelevant to analysis (e.g., titles, footnotes).
•	Dropped non-data rows: The first 6 rows (columns 2–29) and the last ~24 rows included totals, labels, or nulls not usable in analysis.
•	Promoted headers to correctly reflect year and sector labels for alignment and clarity.
•	Renamed key column: Descripción → Sector for better understanding.
•	Filtered nulls in column 2, row 7 to clean inconsistencies.
•	Unpivoted year columns into long format (Sector, Year, GDP_Value) for efficient  analysis.
•	Standardized sector descriptions and corrected inconsistent labels across years columns 1996- 2022.
•	Validated data types: Ensured Year is numeric, and GDP_Value is in float format.
•	Removed duplicates and totals to focus on granular sector-level data. Also applied trimming and check alias rows in numeric columns for accuracy.
________________________________________
✅ Final Dataset Structure:
•	Columns: 3 — Sector, Year, GDP_Value
•	Rows: 433
•	File Name: Panama’s GDP by Economic Activity (1996–2022)
Insights You Can Derive:
•	Fastest-growing sectors post-COVID (e.g. logistics, construction, fintech, tourism).
•	Underperforming or shrinking sectors (for risk mitigation).
•	Sectors contributing the most to GDP and employment (for policy and investment alignment).
________________________________________
### Data source 5
Data Cleaning Summary: Panama’s Annual GDP (2018–2023)
Source: INEC Panama – PIB Anual
Topic: GDP by Economic Activity (Annual)
Unit: Millions of Balboas (B/.)
Period Covered: 2018–2023
Format: CSV
________________________________________
✅ Cleaning Procedures
•	Removed metadata and non-tabular content:
Dropped irrelevant titles, footnotes, and calculated totals from columns 1–2 and the last 3 rows.
•	Eliminated null values:
Removed empty rows (e.g., column 2, row 1) to maintain data integrity.
•	Promoted and renamed headers:
Promoted header rows to reflect actual column names. Renamed "Descripción" to sector for clarity.  
•	Standardized text fields:
Trimmed white spaces, corrected spelling inconsistencies, and ensured consistent naming across sectors.
•	Unpivoted the data:
Transformed year columns (2018–2023) into a long-format structure with columns: sector, Year, and GDP_Value.
•	Validated data types and values:
Ensured Year is integer and GDP_Value is float. Checked for formatting issues like misplaced commas or decimal points.
•	Filtered totals and duplicates:
Removed aggregated total rows and checked for duplicate sector-year entries.
________________________________________
📊 Final Dataset
•	Columns: 3 → sector, Year, GDP_Value
•	Rows: 139 (cleaned and analysis-ready)
•	File Name: Panama’s Annual GDP (2018–2023)

### Data source6

Data Cleaning Summary: Panama’s Provincial GDP (2018–2023)
Source: INEC Panama – PIB Provincial
Topic: GDP by Province
Unit: Millions of Balboas (B/.)
Period Covered: 2018–2023
File Format: CSV
________________________________________
✅ Cleaning Steps:
•	Removed Metadata & Non-Tabular Content:
All introductory rows, footnotes, and subtotals in column 1 were excluded to isolate the actual dataset.
•	Filtered Sector Rows:
In column 2, any rows containing national sectors or categories not related to specific provinces were removed — to focus only on GDP by province.
•	Promoted & Renamed Headers:
The row with actual column names was promoted. The column "Descripción" was renamed to province for clarity.
•	Dropped Irrelevant Columns:
Retained only columns with year-based GDP values and the province name; any non-essential columns were excluded.
•	Reshaped the Data (Unpivoted):
Year columns (2018–2023) were transformed into a long format with three columns: province, Year, GDP_Value — enabling easier time-series analysis.
•	Standardized Province Names:
Cleaned and harmonized province names by fixing typos, trimming whitespace, and ensuring uniform formatting across all rows.
•	Validated Data Types:
Confirmed that Year is stored as an integer and GDP_Value as a float. Cleaned number formatting issues (e.g., commas, decimal symbols).
•	Removed Duplicates:
Duplicate records were removed, and any total or summary rows were filtered out — keeping only value records , year-by-year entries for each province.
________________________________________
📊 Final Dataset Overview:
•	Columns: 3 — province, Year, P_GDP_Value
•	Rows: 60
•	File Name: Panama’s Provincial GDP (2018–2023)



________________________________________
### Data source 6:
Data Cleaning Summary: Panama’s Quarterly GDP (2018–2023)
Source: INEC Panama – PIB Trimestral
Topic: Quarterly GDP by Economic Activity
Unit: Millions of Balboas (B/.)
Period Covered: 2018–2023
File Format: CSV
________________________________________
✅ Cleaning Steps:
•	Removed Metadata and Footnotes:
The first few rows (columns 1 and 2) contained metadata like titles, descriptions, and footnotes that were not part of the tabular data. These rows were removed to ensure the dataset begins with clean, structured values suitable for analysis.
•	Promoted Headers & Renamed Columns:
Promoted the row with the actual Year-Quarter values as headers. Renamed "Descripción" to sector to make the column name more intuitive and analysis-friendly.
•	Excluded Non-Granular Totals and Aggregates:
Rows like "Valor Agregado Bruto", "Impuestos sobre la producción netos" and "Producto Interno Bruto a precios de comprador" (rows 19, 20, 21) were removed. These rows are national-level totals and not individual sector activities. Including them would have caused duplication or skewed sector-level analysis.
•	Filtered Only Sector-Level Records:
Removed totals, summaries, or duplicate groupings to ensure the dataset focused solely on specific economic activity categories. This makes time-series and comparative sector analysis more precise.
•	Unpivoted Wide Data to Tidy Format:
Converted quarter-based columns into rows (long format), resulting in three columns: sector, Quarter, and Q_GDP_Value. This structure supports easier filtering, visualization, and aggregation.
•	Standardized Sector Names:
Cleaned up inconsistent spelling, extra spaces, and symbols — for example, "Otra producción no de mercado (1)" in column row 18— to improve consistency, avoid duplicate groupings, and simplify data filtering.
•	Validated Data Types:
Ensured that the Quarter field is in text format (e.g., 2018Q1) for consistency and Confirmed that Q_GDP_Value is numeric (float), removing thousands of separators and handling currency symbols to ensure smooth calculation and aggregation.
•	Removed Duplicates and Total Rows:
Checked for duplicate records (e.g., repeated sectors for the same quarter) and removed subtotal or total rows to maintain one clean, unique entry per sector per quarter.
________________________________________
📊 Final Dataset Overview:
•	Columns: 3 — sector, Quarter, Q_GDP_Value
•	Rows: 486 ( sector-by-quarter records)
•	File Name: Panama’s Quarterly GDP (2018–2023)
## DAX CODES
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

DAX Calculations
### FDI_Economic_Activity 
DAX
1.	#.Total FDI = SUM('FDI_Economic_Activities'[FDI_Value])
CARD VISUAL.
##.Total FDI 2018–2022 = 
CALCULATE(
    [Total FDI],
    FILTER(
        ALL('BridgeTableYear'),
        'BridgeTableYear'[Year] >= 2018 && 'BridgeTableYear'[Year] <= 2022
    )
)
For sector comparison.
To Track the performance of FDI in panama over the years
(A)	Calculating year-over-year FDI Growth Rate (%).
FDI Growth Rate (%) = 
VAR CurrentYear = SELECTEDVALUE(BridgeTableYear[Year])
VAR PrevYear = CurrentYear - 1

VAR IsInRange = CurrentYear >= 2017 && CurrentYear <= 2023

VAR PrevFDI = 
    CALCULATE(
        SUM(.FDI_By_Economic_Activity[FDI_Value]),
        FILTER(
            ALL(BridgeTableYear),
            BridgeTableYear[Year] = PrevYear
        )
    )

VAR CurrFDI = 
    CALCULATE(
        SUM(.FDI_By_Economic_Activity[FDI_Value]),
        FILTER(
            ALL(BridgeTableYear),
            BridgeTableYear[Year] = CurrentYear
        )
    )

RETURN 
IF(
    IsInRange && NOT ISBLANK(PrevFDI) && PrevFDI > 0,
    DIVIDE(CurrFDI - PrevFDI, PrevFDI) * 100,
    BLANK()
)
Visual.
Line chart
To Determin the Compound Annual growth rate.
FDI 1CAGR (%) = 
VAR StartYear = 2017
VAR EndYear = 2023
VAR NumYears = EndYear - StartYear

VAR StartValue =
    CALCULATE(
        [Total FDI],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = StartYear
        )
    )

VAR EndValue =
    CALCULATE(
        [Total FDI],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = EndYear
        )
    )

VAR CAGR = 
    IF(
        NOT ISBLANK(StartValue) && StartValue > 0 && NOT ISBLANK(EndValue),
        (EndValue / StartValue) ^ (1 / NumYears) - 1,
        BLANK()
    )

RETURN
ROUND(CAGR * 100, 1)
Visual
Table matrix


### FDI_by_top_10_Countres (Top partner countries)
Top Contributing Countries to Panama’s GDP 
DAX:
Total FDI Amount = 
SUM (FDI_by_top_10_Countries [FDI_Value])
CARD VISUAL.
 To track growth performance of FDI Year-over-Year Change (%).
FDI YoY Change % = 
VAR CurrentYear = SELECTEDVALUE(BridgeTableYear[Year])
VAR PrevYear = CurrentYear - 1

VAR CurrentFDI =
    CALCULATE(
        [Total FDI Amount],
        BridgeTableYear[Year] = CurrentYear
    )

VAR PrevFDI =
    CALCULATE(
        [Total FDI Amount],
        BridgeTableYear[Year] = PrevYear
    )

RETURN
IF(
    CurrentYear >= 2017 && CurrentYear <= 2023,
    DIVIDE(CurrentFDI - PrevFDI, PrevFDI, 0),
    BLANK()
)
Visual.
LINE CHART OR METRIX.

### Gross_Value_Added_GVA_by_Economic_Sector.
Dax: 
 Calculating the total gross value added
Total GVA = SUM(Gross_Value_Added__GVA__by_Economic_Sector[GVA_Value])
Visualize with card visual.
To calculate the growth%
measure for calculating Growth % from 2018 to 2022
Growth % 2018–2022 = 
VAR GVA_2018 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = 2018
        )
    )
VAR GVA_2022 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = 2022
        )
    )
RETURN 
IF(
    GVA_2018 > 0,
    DIVIDE(GVA_2022 - GVA_2018, GVA_2018),
    BLANK()
)

Calculating CAGR (Compound Annual Growth Rate) for 2018–2022
CAGR % 2018–2022 = 
VAR StartYear = 2018
VAR EndYear = 2022
VAR NumPeriods = EndYear - StartYear

VAR GVA_2018 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = StartYear
        )
    )

VAR GVA_2022 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Year] = EndYear
        )
    )

RETURN 
IF(
    NOT(ISBLANK(GVA_2018)) && GVA_2018 > 0,
    POWER(GVA_2022 / GVA_2018, 1 / NumPeriods) - 1,
    BLANK()
)
Visual.
 line charts
To Calculate Sector contribution by CAGR%
GVA CAGR % 2018–2022 = 
VAR StartYear = 2018
VAR EndYear = 2022
VAR NumPeriods = EndYear - StartYear

VAR GVA_2018 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = StartYear
        )
    )

VAR GVA_2022 = 
    CALCULATE(
        [Total GVA],
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = EndYear
        )
    )

RETURN 
IF(
    NOT ISBLANK(GVA_2018) && GVA_2018 > 0,
    (POWER(GVA_2022 / GVA_2018, 1 / NumPeriods) - 1),
    BLANK()
)
Visual Bar Chart

### Panama’s GDP by Economic Activity (1996–2022)
Dax:
Calculating Total GDP = SUM('GDP_Economic_Activity'[GDP_Value])
Tracking sectoral performance from 1996-2022
CAGR % 1996–2022 = 
VAR StartYear = 1996
VAR EndYear = 2022
VAR NumPeriods = EndYear - StartYear

VAR GDP_1996 = 
    CALCULATE(
        [Total Sector GDP], 
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = StartYear
        )
    )

VAR GDP_2022 = 
    CALCULATE(
        [Total Sector GDP], 
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = EndYear
        )
    )

RETURN 
IF(
    NOT ISBLANK(GDP_1996) && GDP_1996 > 0,
    POWER(GDP_2022 / GDP_1996, 1 / NumPeriods) - 1,
    BLANK()
)

Visual.
Stacked bar chart.
Tracking sectoral performance from 2018-2022
1CAGR % 2018–2022 = 
VAR StartYear = 2018
VAR EndYear = 2022
VAR NumPeriods = EndYear - StartYear

VAR GDP_2018 = 
    CALCULATE(
        [Total Sector GDP], 
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = StartYear
        )
    )

VAR GDP_2022 = 
    CALCULATE(
        [Total Sector GDP], 
        FILTER(
            ALL('BridgeTableYear'),
            'BridgeTableYear'[Yearly] = EndYear
        )
    )

RETURN 
IF(
    NOT ISBLANK(GDP_2018) && GDP_2018 > 0,
    (POWER(GDP_2022 / GDP_2018, 1 / NumPeriods) - 1) * 100,
    BLANK()
)


### Panama’s_Annual_GDP__2018_2023:
Dax:
Calculating Total Annual GDP:
Total GDP 2018-2023 = 
CALCULATE(
    SUM('Panama’s_Annual_GDP__2018_2023'[GDP_Annual_Value]),
    FILTER(
        'Panama’s_Annual_GDP__2018_2023',
        'Panama’s_Annual_GDP__2018_2023'[Year] >= 2018 &&
        'Panama’s_Annual_GDP__2018_2023'[Year] <= 2023
    )
)
calculate the GDP Growth Rate (%).
GDP Growth Rate (%)2 = 
VAR CurrentYear = SELECTEDVALUE(BridgeTableYear[Year])

VAR CurrentGDP = 
    CALCULATE(
        SUM('Panama’s_Annual_GDP__2018_2023'[GDP_Annual_Value]),
        FILTER(
            ALL('Panama’s_Annual_GDP__2018_2023'),
            'Panama’s_Annual_GDP__2018_2023'[Year] = CurrentYear
        )
    )

VAR PreviousGDP = 
    CALCULATE(
        SUM('Panama’s_Annual_GDP__2018_2023'[GDP_Annual_Value]),
        FILTER(
            ALL('Panama’s_Annual_GDP__2018_2023'),
            'Panama’s_Annual_GDP__2018_2023'[Year] = CurrentYear - 1
        )
    )

RETURN
IF(
    NOT(ISBLANK(CurrentGDP)) && NOT(ISBLANK(PreviousGDP)) && PreviousGDP <> 0,
    DIVIDE(CurrentGDP - PreviousGDP, PreviousGDP),
    BLANK()
)
Visual.
line chart

### Panama Provincial_GDP_2018–2023:
Dax:
Calculating Top panama’s Provinces by Total GDP.
Total_GDP_By_province = SUM('Provincial_GDP'[GDP_Value]).

Province GDP by Year over Year Growth.
GDP_YoY = 
VAR CurrentYear = MAX('BridgeTableYear'[Year])
VAR PrevYear = CurrentYear - 1
VAR CurrGDP =
    CALCULATE(
        [Total_GDP],
        'BridgeTableYear'[Year] = CurrentYear
    )
VAR PrevGDP =
    CALCULATE(
        [Total_GDP],
        'BridgeTableYear'[Year] = PrevYear
    )
RETURN
    DIVIDE(CurrGDP - PrevGDP, PrevGDP)

Visual.
Map of panama

#.7 Panama’s_Quarterly_GDP_2018–2023.
DAX:
Caculating the Average GDP By Quarter
Avg_GDP_By_Quarter = 
AVERAGEX(
    VALUES(BridgeTableQuarter[Quarters]),
    CALCULATE(SUM('Panama’s_Quarterly_GDP__2018_2023'[Quarter_GDP_Value]))
)

Visual.
Line chart.
Tracking Quarter growth 
Quarterly_GDP_Growth_% = 
VAR CurrentQ = SELECTEDVALUE(BridgeTableQuarter[Quarters])
VAR IsInRange = 
    CurrentQ >= "2018Q1" && CurrentQ <= "2024Q3"

VAR PrevQ = 
    CALCULATE(
        MAX(BridgeTableQuarter[Quarters]),
        FILTER(
            ALL(BridgeTableQuarter),
            BridgeTableQuarter[Quarters] < CurrentQ
        )
    )

VAR CurrGDP = 
    CALCULATE(
        SUM('Panama’s_Quarterly_GDP__2018_2023'[Quarter_GDP_Value]),
        TREATAS({CurrentQ}, 'BridgeTableQuarter'[Quarters])
    )

VAR PrevGDP = 
    CALCULATE(
        SUM('Panama’s_Quarterly_GDP__2018_2023'[Quarter_GDP_Value]),
        TREATAS({PrevQ}, 'BridgeTableQuarter'[Quarters])
    )

RETURN
IF(
    IsInRange && NOT ISBLANK(PrevGDP),
    DIVIDE(CurrGDP - PrevGDP, PrevGDP),
    BLANK()
)
visual
Table matrix
# DAX MODELLING AND RELATIONSHIPS
![Captura de pantalla 2025-06-14 192436](https://github.com/user-attachments/assets/c54f0974-626e-4997-96b6-3b33a826990f)
![Captura de pantalla 2025-06-14 192750](https://github.com/user-attachments/assets/da027f69-a16e-4d1b-b0bd-67c606cda249)
# PRESENTATION
[![Slide Preview](./slide-preview.png)](./powerpoint%20data%20presentation.pptx)
🔗 [Click here to download the full PowerPoint presentation](./powerpoint%20data%20presentation.pptx)
# DASHBOARD
[📈 View Dashboard](<iframe title="power bi panama growth analysis" width="600" height="373.5" src="https://app.powerbi.com/view?r=eyJrIjoiZWM5MjIxOGQtNGQ0Yi00MzEyLWI1YjEtNzU3ZjgxZTJjYzk4IiwidCI6IjVmNTY2NGU1LWYzNjktNDliYi1hZjRjLWU0YTVkMmRmNTRhNyIsImMiOjJ9" frameborder="0" allowFullScreen="true"></iframe>)

)
