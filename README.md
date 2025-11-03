# ElectViz: Indian General Election Analysis Dashboard (2009-2024)

---

### **Table of Contents**
1.  [**About This Project**](#about-this-project)
2.  [**Key Features**](#key-features)
3.  [**Tech Stack**](#tech-stack)
4.  [**Data Model**](#data-model)
5.  [**Installation & Usage**](#installation--usage)
6.  [**Project Structure**](#project-structure)
7.  [**Future Enhancements**](#future-enhancements)
8.  [**Author**](#author)

---

### **About This Project**

**ElectViz** is a comprehensive Power BI dashboard that transforms raw, fragmented Indian General Election results from four major cycles (2009, 2014, 2019, 2024) into a unified, interactive, and insightful analytical tool.

The primary challenge with this data is its fragmentation across multiple files and inconsistencies in naming (states, parties). This project solves that problem through a robust **ETL (Extract, Transform, Load)** pipeline built in Power Query, creating a single, reliable source of truth. The dashboard then uses this clean data to visualize national and state-level results, party performance, and long-term voting trends.

This tool is designed for political analysts, journalists, researchers, and students who need to explore, filter, and understand India's complex electoral landscape without needing to perform manual data cleaning.

### **Key Features**

* **Multi-Page Interactive Report:**
    * **Page 1: National Overview:** High-level KPIs (Total Seats, Turnout), geographic map of state-wise winners, and top party performance.
    * **Page 2: State-Level Analysis:** A drill-down page to select a single state and see all constituency winners, party seat counts, and state-specific turnout.
    * **Page 3: Party Performance Deep Dive:** Select a party to analyze its seat and vote share trends over the four election cycles.
    * **Page 4: Voter & Constituency Insights:** An analytical sandbox to explore victory margins, voter turnout correlations, and identify the closest races.

* **Dynamic DAX Measures:**
    * Calculates complex metrics on-the-fly, such as `Vote Share %`, `Seat Change vs. Previous Election`, and `Winning Party by State`.
* **Time-Series Analysis:**
    * Visualizes trends in seat counts and vote share from 2009 to 2024.
* **Robust ETL Pipeline:**
    * Cleans, standardizes, and appends four separate data files into a single master table (`Election_Data`).
    * Derives a `Year` column, standardizes `Party` and `State` names, and cleans text data.

### **Tech Stack**

* **Visualization & Modeling:** Microsoft Power BI Desktop
* **ETL (Data Transformation):** Power Query (M Language)
* **Analytical Calculations:** DAX (Data Analysis Expressions)

### **Data Model**

The project uses a simple, single-table model for speed and simplicity in this specific context. All visuals are powered by the consolidated `Election_Fact` table, which is the output of the Power Query append process.

**`Election_Fact` (Fact Table)**
* Year
* State
* Constituency
* Party
* Winning_Candidate
* Votes
* Electors
* Turnout
* Margin
* Margin_Perc

### **Installation & Usage**

To use this report:

1.  **Prerequisites:** You must have **Microsoft Power BI Desktop** installed (it's a free download from the Microsoft Store).
2.  **Download:** Download the `ElectViz.pbix` file from this repository.
3.  **Open:** Open the `ElectViz.pbix` file in Power BI Desktop.
4.  **Explore:**
    * Use the slicers on each page to filter the data.
    * Click on any chart element (like a state on the map or a bar in a chart) to cross-filter the entire page.
    * Navigate between the pages (tabs at the bottom) to explore different levels of detail.
### **Project Structure**
ElectViz_Project/ │ ├── Data/ │ ├── India_PC_2009.csv │ ├── India_PC_2014.csv │ ├── India_PC_2019.csv │ └── India_PC_2024.csv │ ├── PowerBI_Project/ │ └── ElectViz.pbix │ └── README.md

### **Future Enhancements**

* **Star Schema:** Refactor the single-table model into a proper star schema (with `dimParty`, `dimState`, `dimDate` dimensions) for improved performance and scalability.
* **Historical Expansion:** Integrate pre-2009 election data, which would require a complex mapping to account for the 2008 constituency delimitation.
* **Demographic Overlay:** Blend in census data to correlate voting patterns with constituency demographics (e.g., literacy, urban/rural).

### **Author**

* **Dishant Gangwar**
*  MIT License
