# Cloudera Octopai Data Lineage

## Hands-On Lab Exercises

## Exercise #1

**Root Cause Analysis (RCA)**

**Context**: Assume you’re looking at a report and something doesn’t add up — a KPI seems off.
1. Navigate to the **E2E Lineage Dashboard** by clicking the <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/09e0a4b8-5bb6-410a-984d-259a4ec17520" />
 icon.
2. Search for the column **TotalProductCost** in the table **DwhFactSales**.
3. Open the **E2E Column Lineage** by clicking the <img width="28" height="29" alt="image" src="https://github.com/user-attachments/assets/14bd107b-8b08-4db0-9b3f-fca1265dd44b" />
icon.
4. Move upstream to the **SSIS** package **Load STG**.
5. Click the <img width="12" height="18" alt="image" src="https://github.com/user-attachments/assets/18ba540b-dc08-457b-9d2b-dc44cdce8849" />
 icon next to the transformation logic **populate stgFactPurchasing** and select the **Inner System Lineage** icon <img width="26" height="24" alt="image" src="https://github.com/user-attachments/assets/4dbe7960-68d7-44bc-b0c2-2ec5a7584bf1" />
.
6. Locate the **MRRSALESORDERS** component and select the **TotalProductCost** column.
7. Double-click the **MRRSALESORDERS** header and review the calculation on Line 12 of the component script.
8. Go back to **E2E Column Lineage** via the "Go back" function of your browser and select the **Knowledge Hub** icon <img width="25" height="21" alt="image" src="https://github.com/user-attachments/assets/c0c87375-9de5-42f0-9f1c-fea8c027a8d4" />
 for the **TotalProductCost** column in the **STGFACTSALES** table. You can find it in within **Load STG** --> **populate StgFactPurchasing** --> **STGFACTSALES** 
9. Review Description and Technical Description of the asset. Did you spot the error in the SQL script?
10. Impact Analysis: Shortcut back to **E2E** and open click on **E2E_Stg_Sales** --> **DBO** --> **StgFactSales** --> **TotalProductCost** and see the highlighted Column and its origins. This can be useful for further Root Cause Analyses 
 of the **DhwFactSales** table.

**Benefit**: Octopai reduces RCA time from days to minutes, increasing confidence in data integrity and improving efficiency.
# 
## Exercise #2
**Schema Change / Impact Analysis**

**Context**: Imagine you’re planning a schema update—what happens to everything downstream?

1. Open **Discovery** <img width="37" height="29" alt="image" src="https://github.com/user-attachments/assets/10cc79f9-e56b-49ed-8f64-e084e609c62e" />
 and search for the column name **EmailAddress**.
2. Review results under **SQL Server → Columns**.
3. Use smart grouping and filtering to narrow down results; export to CSV for a historical copy of the results.
4. Go to the **Cross System Lineage Dashboard** <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/85056571-98e7-4c00-82ff-38551f8dc2f8" />
 and search for the **EmailAddress** table using the **Person** schema <schema name.table> in the top search bar.
5. Hover over the table and click on the Cross System Lineage <img width="28" height="31" alt="image" src="https://github.com/user-attachments/assets/27411666-1939-45f6-9bce-9b4c65e5cde3" />
 icon. Here you can see all downstream components referencing to this schema. This will help you when you have to change this schema.
6. Use **Cross System Lineage** <img width="23" height="25" alt="image" src="https://github.com/user-attachments/assets/cb83e796-b82e-4379-8479-93e38c950a26" />
 in the radial menu of objects to discover further dependencies of one of the other downstream elements. You will always see Person.EmailAddress as one of many components. 
7. Navigate to the **E2E Lineage Dashboard** <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/c6b95f95-183e-43a7-b2b4-1b03f8dd14c9" />
 and search for **EmailAddress**.
8. Under the **DB Objects** section, locate the table with the **Person** schema, **EmailAdress** table name and **EmailAddress** column.
9. Click on the **E2E Column Lineage** <img width="28" height="29" alt="image" src="https://github.com/user-attachments/assets/df487676-5220-423a-9d68-b7e5150bbc73" />
 icon. Now, you can see the lineage of a single column over all systems. If you plan changes of this column, you could now examine the impact on downstream components.

**Benefit**: Octopai reduces risks of change management activities and empowers proactive teams.
# 
## Exercise #3
**Compliance & Governance**

**Context**: An auditor requests a trace of where PII flows across your environment.

1. Navigate to the **E2E Lineage Dashboard** by clicking the <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/ea13c382-b789-40ef-a8b9-883241f63208" />
 icon and search for **EmailAddress**.
2. Hover over one of **PERSON-->EmailAddress** report and click the **E2E Column Lineage** <img width="28" height="29" alt="image" src="https://github.com/user-attachments/assets/0703281a-6c88-46b5-bf5a-2c44696de908" />
 icon.
3. Review the path from CRM → ETL → DWH → BI Report (from left to right). Even though this example is hold simple (on purpose), it still shows you the path of a single column through multiple different tools. If a BI Report is broken, you can usually see here where to search for potential breaking changes.
4. Go to the **vEmployee** component in the ETL, click <img width="12" height="18" alt="image" src="https://github.com/user-attachments/assets/cbfe525b-4593-4e58-9480-c7a02b1b0f40" />
 and then select **Inner System Lineage** to review the ETL script. This view can help you finding misconfigured ETL scripts from one single pane of tool.
5. Return to **E2E Column Lineage** by using the **Go Back** function of your browser
6. Go to the farthest upstream object and find the **EmailAddress** column (part of the **EmailAddress** table). Click the <img width="12" height="18" alt="image" src="https://github.com/user-attachments/assets/741170c1-a298-496c-b395-f31f96126d64" />
 and select **Override Column Lineage** to view additional downstream objects. This way, you don not only see the single path from **AdventureWorks2014** SQLServer Database to the **EmployeePersonalInfo** report we selected in Step 2 but also all other parallel lines that are using this **EmailAddress** column in any way.
7. Open the **Knowledge Hub** <img width="27" height="34" alt="image" src="https://github.com/user-attachments/assets/47dbd020-d2bb-4ba3-8983-a59c4efb24e6" />
 and search for **EmailAddress**.
8. Explore results using filters, glossary, and tags. You can maintain multiple properties here for each Asset
9. Export Total Assets to CSV by clicking the <img width="21" height="22" alt="image" src="https://github.com/user-attachments/assets/4de973ac-b4ae-4b76-906a-3538813de453" />
 icon at the top of the Total Assets list for an audit-ready report.

**Benefit**: Octopai simplifies compliance requests by making them automated and traceable.
# 
## Exercise #4
**Cloud Migration**

**Context**: Before migrating to the cloud, you need to know what’s connected to what and reduce unnecessary objects.

1. Navigate to **Discovery** <img width="37" height="29" alt="image" src="https://github.com/user-attachments/assets/ac282603-8749-4a4b-9d09-abe40b0cbe39" />
 and search for **FactSales**.
2. List **Informatica Table Targets** and compare them to **SSIS Table Targets**.
3. Identify assets with dependencies and usage using **Cross System Lineage**.
   a. Investigate lineage for the **Table Targets** listed in **Discovery**.
   b. Open **Cross System Lineage Dashboard** <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/94c2afc3-0d53-4705-b2aa-e9725b45e4f1" />
 and search for **DwhFactSales**.
   c. Hover over the **DwhFactSales** table and click the <img width="28" height="31" alt="image" src="https://github.com/user-attachments/assets/185a2164-f004-4e65-8f7d-4851547808cf" />
 icon.
   d. Note the two ETLs feeding the **DwhFactSales** table.
   e. Hover over each of both ETLs, click on the arrow to the left and the arrow to the right to see all **Downstream and Upstream Objects** for both ETLs. This view helps you seeing all dependencies before migrating one of the two ETLs to the Cloud. 
   Let's see how it would look like if prepare a migration of one **SSIS ETL job** to **Redshift**. For this, we will search for another, more clear example:
4. Reset the **Discovery** page by clicking the <img width="21" height="20" alt="image" src="https://github.com/user-attachments/assets/3eabeedf-3c18-4e2b-a9b8-ff9bc1d27760" />
 icon.
5. Search for **TotalProductCost** and select **SQL Commands** under **SSIS** section.
6. Click on the first SQL Scripts in the column **SQL Script** and then click on the <img width="26" height="29" alt="image" src="https://github.com/user-attachments/assets/0d1f5a24-2284-4ce2-b053-91d7ccf2f277" />
 icon.
7. Click the **Octomize** tab and then select **Migration Assistance**.
   IMPORTANT: After changing the SQL commands and trying stuff out, due to a bug, it can be that you need to click on Octomize AI --> Optimization and Re-Run the Optimization job. Then you should see the changes.
9. Select **SQL Server** (which is **SSIS**) in the **From Vendor** box and **Redshift** in the **To Vendor** box.
10. Click on the play icon and review the script conversion. Octopai will show you guidance on a possible migration. You will see that you do not only get a Redshift version but also detailled comments on things to consider when migrating. 

**Benefit**: Octopai enables informed migrations with full visibility, optimization guidance and script conversion.

Bonus material: Feel free to explore what happense when you change statements within **Live Lineage** on the left hand side within the SQL Server ETL Job. If you change it, you can not only see Interpretation, Optimization and Error Detection within Octomize AI but also see how the Flow changes and how Lineage-Based error (e.g. orphaned columns) arise. See the following three screenshots where I changed **UnitPrice** to **UnitPriceDSHFLKDSNFLDKSFNDSLKFNDSLKFNDLSKFNLD**

<img width="1510" height="949" alt="Live Lineage 1" src="https://github.com/user-attachments/assets/01eebf3d-2947-40c4-929a-54bb5d3e0178" />
<img width="1559" height="1248" alt="Live Lineage 2" src="https://github.com/user-attachments/assets/4db60d33-8c38-4265-af12-eb693fb29dac" />
<img width="1554" height="690" alt="Live Lineage 3" src="https://github.com/user-attachments/assets/d50548cb-8797-43e1-872a-04ed44b2649e" />


# 
## Exercise #5
**FinOps / Cost Reduction**

**Context**: You’ve been asked to reduce waste/cost by showing unused or duplicate reports and data pipelines.

1. Navigate to **Discovery** <img width="37" height="29" alt="image" src="https://github.com/user-attachments/assets/ff01c9f3-3e02-4a22-b356-eacd62908cdb" />
 and search for the ETL/Package name **Load STG**.
2. Go to **SSIS** and click on **SQL Commands**, show 50 items per page and then group by **Package Name**. Drag a column header and drop under **Collapse All**  to group by that column.
3. Note that there are two packages doing the same thing and it may make sense to remove one after verification (e.g., download as CSV and compare).
4. The same can be done with reports to identify duplicate or unnecessary instances.
5. Navigate to the **Cross System Lineage Dashboard** <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/b52d49cb-4f78-433e-9587-dfe8ff201f72" />
 and search for **DwhFactSales**.
6. Hover over the first table object (**E2E_Dwh_Sales.dbo.DwhFactSales**) and select **Cross System Lineage** <img width="28" height="31" alt="image" src="https://github.com/user-attachments/assets/072a40f9-8e74-4391-a5d4-16743558eb47" />
.
7. Notice several dashboards that use identical datasets. This suggests reporting duplication—one of the most common hidden cost drivers in cloud BI.
8. From a FinOps and governance perspective it may be desirable to send to consumer groups to see if these can be cleaned up. Which ones are being used?

**Benefit**: Octopai enables intelligent rationalization by revealing redundant data flows, disconnected pipelines, and redundant reporting logic—helping FinOps teams drive measurable cost reductions without sacrificing data availability.
# 
## Exercise #6
**Data Democratization**

**Context**: Enable new employees and non-technical users. They need to understand a particular metric.

1. Navigate to the **Knowledge Hub** <img width="27" height="34" alt="image" src="https://github.com/user-attachments/assets/0dd45f48-60e1-49a6-92fb-28d8fed730df" />
 and search for **TotalProductCost**.
2. Under **Filters** <img width="23" height="22" alt="image" src="https://github.com/user-attachments/assets/3f89b215-efc0-41de-bbe9-ff9001055f43" />
 and **Status**, uncheck **Select All** and select **Approved**, then click **Apply**.
3. Filter further by system type by clicking the <img width="24" height="21" alt="image" src="https://github.com/user-attachments/assets/8c5284b5-d288-49cd-8f62-b020f77710b6" />
 icon and selecting SQL Server or PowerBI.
4. Review business terms, glossary notes, owner, etc. of assets listed.
5. **Advanced Search** can be used to narrow results down further.
<img width="243" height="142" alt="image" src="https://github.com/user-attachments/assets/cc68bb17-f544-4d5f-8646-a8243088b503" />

**Benefit**: Octopai bridges technical and business knowledge, empowering faster, more confident decision-making.
