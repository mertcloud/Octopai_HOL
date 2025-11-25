# Cloudera Octopai Data Lineage

# Hands-On Lab Exercises

# Exercise #1

Root Cause Analysis (RCA)
Context: Assume you’re looking at a report and something doesn’t add up—a KPI seems off.

Script:
- Navigate to the E2E Lineage Dashboard by clicking the  icon.
- Search for the column TotalProductCost in the table DwhFactSales.
- Open the E2E Column Lineage by clicking the   icon.
- Move upstream to the SSIS package Load STG.
- Click the  icon next to the transformation logic populate stgFactPurchasing and select the Inner System Lineage icon .
- Locate the MRRSALESORDERS component and select the TotalProductCost column.
- Double-click the MRRSALESORDERS header and review the calculation on Line 12 of the component script.
- Go back to E2E and select the Knowledge Hub icon  for the TotalProductCost column in the StgFactSales table.
- Review Description and Technical Description of the asset.
- Impact Analysis: Shortcut back to E2E and open the Cross System Lineage of the DhwFactSales table.

Benefit: Octopai reduces RCA time from days to minutes, increasing confidence in data integrity and improving efficiency.
