# Patient Summary Report

### Dashboard Link : https://app.powerbi.com/reportEmbed?reportId=ae9ec6f6-b093-4b56-a0ee-c38caa3ca599&autoAuth=true&ctid=a9e4cffe-f9c4-4d40-8d17-f43b98bb3f3f

## Problem Statement

This report provides a summary of patient visits categorized into Inpatients, Outpatients, and Day Cases. It helps in understanding patient trends, service efficiency, and areas for improvement in healthcare facilities.

Inpatients (Admitted Patients): These patients require overnight or extended hospital stays. Monitoring their average stay duration and readmission rates is crucial for improving care quality.

Outpatients (Non-Admitted Patients): Patients who visit for consultations, treatments, or minor procedures. Key focus areas include appointment efficiency and waiting time reduction.

Day Case Patients: Patients who undergo procedures or treatments and are discharged on the same day. Ensuring smooth discharge processes and post-treatment follow-ups is essential.


### Steps followed 

- Step 1 : Loaded **CSV dataset** into **Power BI Desktop**.
- Step 2 : Opened **Power Query Editor** and enabled:
   - "Column Distribution"
   - "Column Quality"
   - "Column Profile"
- Step 3 : Set "Column Profiling" to scan the **entire dataset**.
- Step 4 : Identified and handled missing values in **Arrival Delay** column:
   - **Ignored null values** in calculations since they were less than **1% of total data**.
   
### **Report Design & Visualization**

- Step 5 : Selected an appropriate **theme** for the report.
- Step 6 : Added **Visual Filters (Slicers)** for key fields:
   - **Patient Type (Inpatient, Outpatient, Day Case)**
   - **Specialty (Orthopaedics, Cardiology, etc.)**
   - **Age Group (0-15, 16-64, 65+)**
- Step 7 : Used **Card Visuals** to display key metrics:
   - **Total Patients in Last Month’s Waiting List**: **708,729**
   - **Previous Year’s Waiting List Count**: **640,441**
   - **Growth in Waiting List**: **Increased**
- Step 8 : Created a **Bar Chart** for waiting times:
   - **0-3 months, 3-6 months, 6-9 months, 9-12 months, 12-18 months, and 18+ months**.
- Step 9 : Added a **Pie Chart** to visualize patient distribution across categories.
### **DAX Calculations**
- Step 11. Created **calculated columns** for:
   - **Age Group Segmentation**:
     ```DAX
     Age Group =
       IF(Patients[Age]<=15, "0-15",
       IF(Patients[Age]<=64, "16-64", "65+"))
     ```
- Step 12. Created **Measures** for:
   - **Total Patient Count**:
     ```DAX
     Total Patients = COUNT(Patients[PatientID])
     ```
   - **Percentage of Patients in Each Category**:
     ```DAX
     % Patients = (COUNT(Patients[PatientID]) / TOTALCOUNT(Patients[PatientID])) * 100
     ```

## **Insights from the Report**

### **1. Total Patient Distribution**
- **Total Patients**: **2,464,096**
- **Outpatients**: **2,173,739 (88.2%)**
- **Inpatients & Day Cases Combined**: **1,051,979 (42.7%)**

### **2. Specialty-Wise Patient Count (Example: Orthopaedics)**
- **Total Orthopaedics Patients**: **8,485**
  - **Day Cases**: **5,505**
  - **Inpatients**: **4,915**
  - **Outpatients**: **74,436** (majority)

### **3. Age Group Analysis**
- **0-15 Years**: **15.3% of total patients**
- **16-64 Years**: **56.8% of total patients** (majority)
- **65+ Years**: **27.9% of total patients** (longer waiting times observed)

### **4. Waiting Time Insights**
- **Highest patient volume in the 0-3 month waiting period.**
- **Significant backlog in the 18+ month category, especially for 65+ age group.**

### **5. Growth in Waiting List**
- **2021 vs. 2020:** Increased by **~10.7%**.
- **Major backlog areas:** **Inpatients (Elective Surgeries) & Specialist Outpatients**.

---

## **Recommendations**
- **Optimize Outpatient Scheduling:** Reduce wait times by **enhancing appointment booking efficiency**.
- **Improve Resource Allocation:** Better distribution of **beds and staff for inpatients**.
- **Focus on High-Wait Specialties:** Prioritize backlogs in **Orthopaedics, Cardiology, and Oncology**.
- **Implement Digital Follow-ups:** Reduce unnecessary in-person visits for stable outpatients.
- **Increase Senior Patient Priority:** Address delays for the **65+ age group** by **expanding specialist care access**.

---

## **Snapshots of the Dashboard**
### **Power BI Service Dashboard:**
![Dashboard_Snapshot](https://github.com/user-attachments/assets/503f485b-c3a3-4846-a4c7-5fa59567a032)
![Dashboard_Snapshot](https://github.com/user-attachments/assets/d66bd2f1-bbbf-41b1-bc94-060083042972)
![Dashboard_Snapshot](https://github.com/user-attachments/assets/f3a0d336-3541-4a27-a402-7ff7585089fa)

### **Power BI Desktop Report View:**
![Report_Snapshot](https://github.com/user-attachments/assets/4e509ecd-8e6c-49c8-883a-08bf86d5991f)
![Report_Snapshot](https://github.com/user-attachments/assets/d659d8f7-a3b9-48aa-b8e4-28b0fd5b23ec)

---

## **Conclusion**
The report highlights key patient statistics, trends, and backlog areas in healthcare facilities. By implementing **better scheduling, resource management, and patient prioritization**, hospitals can enhance efficiency and **reduce waiting times**. Future reports can integrate **predictive analytics** to forecast patient demand and improve **hospital resource planning**.
