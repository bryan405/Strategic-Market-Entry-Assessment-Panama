

# Strategic-Market-Entry-Assessment-Panama

## 📚 Table of Contents

1. [👤 About Me](#-about-me)  
2. [💼 Business Request](#-business-request)  
3. [🧹 Data Cleaning](#-data-cleaning)  
4. [📊 Presentation](#-presentation)  
5. [📈 Dashboard](#-dashboard)  
6. [🧠 DAX Modelling & Relationships](#-dax-modelling--relationships)  
7. [🗂️ Data Source](#-data-sources)  

# [👤 About Me](#-about-me)
From selling electronics on the buzzing streets of Nigeria to managing mouthwatering empanadas in Panama —and now uncovering insights through data—I’ve had quite the journey!
I’m a versatile professional with over 7 years of experience in sales, hands-on leadership in food production and marketing, and an academic background in Biology, Biotechnology (B.Sc.), and Food Safety (M.Sc.). My passion for problem-solving, systems thinking, and business strategy naturally led me to the world of data analytics.
Now, I'm helping businesses make smarter decisions through data. I turn messy datasets into actionable insights, build dashboards that actually tell stories, and use analytics to solve real-world problems—especially in sales, marketing, and food safety domains.
[Click here for preview](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/commit/1301b49a63a68abb9001eee94e44119395e76e20)
# [💼 Business Request](#-business-request)
### project overview
We are Dajcom Limited, a leading company in the home appliances, food, and beverage industry. As we explore strategic opportunities to expand our operations into Panama, we are seeking your expertise to support us with a market analysis that will guide our investment and entry decisions.
[Click here for previeiew](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/raw/refs/heads/main/project%20overview.docx)

 # [🧹 Data Cleaning](#-data-cleaning) 
Dataset no:1
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
[Click here for full detail](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/raw/refs/heads/main/Data%20cleaning%20documentation.docx)

# [📊 Presentation](#-presentation)
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


