# Cloudera Octopai Data Lineage

Hands-On Lab Exercises

# Exercise #1

Root Cause Analysis (RCA)
Context: Assume you’re looking at a report and something doesn’t add up — a KPI seems off.
1. Navigate to the E2E Lineage Dashboard by clicking the <img width="43" height="43" alt="image" src="https://github.com/user-attachments/assets/09e0a4b8-5bb6-410a-984d-259a4ec17520" />
 icon.
2. Search for the column TotalProductCost in the table DwhFactSales.
3. Open the E2E Column Lineage by clicking the <img width="28" height="29" alt="image" src="https://github.com/user-attachments/assets/14bd107b-8b08-4db0-9b3f-fca1265dd44b" />
icon.
4. Move upstream to the SSIS package Load STG.
5. Click the <img width="12" height="18" alt="image" src="https://github.com/user-attachments/assets/18ba540b-dc08-457b-9d2b-dc44cdce8849" />
 icon next to the transformation logic populate stgFactPurchasing and select the Inner System Lineage icon <img width="26" height="24" alt="image" src="https://github.com/user-attachments/assets/4dbe7960-68d7-44bc-b0c2-2ec5a7584bf1" />
.
6. Locate the MRRSALESORDERS component and select the TotalProductCost column.
7. Double-click the MRRSALESORDERS header and review the calculation on Line 12 of the component script.
8. Go back to E2E and select the Knowledge Hub icon  for the TotalProductCost column in the StgFactSales table.
9. Review Description and Technical Description of the asset.
10. Impact Analysis: Shortcut back to E2E and open the Cross System Lineage of the DhwFactSales table.

Benefit: Octopai reduces RCA time from days to minutes, increasing confidence in data integrity and improving efficiency.
