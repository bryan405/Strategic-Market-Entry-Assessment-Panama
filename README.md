

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
    [Click here for full detail](https://github.com/bryan405/Strategic-Market-Entry-Assessment-Panama/raw/refs/heads/main/DAX%20CODES.docx)

    
![Captura de pantalla 2025-06-14 192436](https://github.com/user-attachments/assets/44995f4f-5053-48e9-a22b-0a0e1337d3f2)
![Captura de pantalla 2025-06-14 192750](https://github.com/user-attachments/assets/2d18b783-f847-484e-83fb-5cf873532574)

 # [🗂️ Data Source](#-data-sources)


