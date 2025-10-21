# Student-dashboard
# Student Record Analysis & Visualisation

![YABATECH Student Record Dashboard](images/dashboard.png)


Dashboard snapshot
- Image: images/dashboard.png  
- Alt text: "YABATECH Student Record Dashboard showing KPIs, filters, charts and maps"

Key highlights shown on the dashboard (visible in the snapshot)
- Total Graduates: 9,776  
- Total Admitted: 20,000 (20K)  
- Average CGPA: 1.99  
- Total Failed: 10,000 (10K)  
- Total Withheld: 116  
- Total Dropout: 107

What the dashboard contains
- KPI cards for high-level metrics (graduates, admitted, average CGPA, failed, withheld, dropout)
- Slicers/filters: Gender, Admission Year, Department, Scholarship Status, Faculty
- Charts:
  - Final CGPA by Age at Admission (bar)
  - Graduation Rate by Faculty and Department (clustered chart)
  - Final CGPA by Department (bar)
  - Graduation Rate by Faculty (matrix/treemap style)
  - Admission & Graduation maps by State of Origin (map visuals)
  - Gender breakdown (donut/pie)
  - Total Admitted by Admission Year (line chart)

Data schema (fields used by the dashboard)
- student_id (string) — ID
- admission_year (integer)
- faculty (string)
- department (string)
- gender (string) — values: "Male", "Female", etc.
- cgpa (numeric) — 0.00 to 4.00
- status (string) — e.g., "Graduated", "Failed", "Withheld", "Dropout"
- scholarship_status (string) — "Yes" / "No"
- state_of_origin (string) — Nigeria states (aggregated)
- age_at_admission (integer) or age_group (string)


- powerbi/
 
How the dashboard was built (high level)
1. Data preparation in Excel
   - Imported and cleaned the original export(s).
   - Removed duplicates.
   - Normalised categorical values (faculty/department names).
   - Created derived columns: age_at_admission or age_group, cohort, pass/fail flags.
   - Exported to CSV for Power BI import (or used Power Query inside Power BI).

2. Modelling & measures in Power BI Desktop
   - Import CSV into Power BI Desktop and confirm data types.
   - Create relationships if using multiple tables (e.g., student table + lookup tables).
   - Create calculated columns and measures (examples below).
   - Build visuals and format cards, color palette, and slicers.
   - Export the dashboard or individual visuals to PNG for the repo.

 DAX measures 
- Total_Admitted = COUNTROWS(Students)
- Total_Graduates = CALCULATE(COUNTROWS(Students), Students[status] = "Graduated")
- Average_CGPA = AVERAGE(Students[cgpa])
- Graduation_Rate = DIVIDE([Total_Graduates], [Total_Admitted], 0)


Contact / Repro questions
- Author: Olatundun25 (GitHub)  
