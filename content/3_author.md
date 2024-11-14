---
title: Splitting, Clustering and Joining
nav: Splitting, Clustering and Joining
gallery: true
---

<br>

Looking first at the `creator` field, let's use OpenRefine’s clustering feature to identify and merge similar but non-identical values across a large dataset.

### Split the Creator Field into Individual Names

{% include alert.html text="Note: You will only need to do this step  and the final joining step with columns that contain multiple items separated by semi-colons" color="light" align="center" %}

a. **Select the Creator Column**: In the column menu for the creator field, click the dropdown.

b. **Choose “Edit cells” > “Split multi-valued cells…”**: 
   - Enter `;` as the separator to split each name into its own cell within the same column.
   - This will separate names like “Painter, Charles G.; Simpson, William Ray; Parks, F.P.” into three individual rows for each name.

### Formatting

Before we cluster, I am noticing that many of the discrepancies between the author names are due to inconsistent whitespace. To correct these items or adjust for upper / lowercasing inconsistencies:

### Lowercasing and Removing Whitespace

a. In the column menu (e.g., location name), choose **“Edit cells”** > **“Transform…”**.

b. **Enter transformations** in GREL (General Refine Expression Language) to standardize formats:

   - To make all entries title case (capitalizing each word): Use `value.toTitlecase()`.
   - To make entries lowercase: Use `value.toLowercase()`.
   - To trim extra whitespace: Use `value.trim()`.

### Clustering

a. Click on the **drop-down menu** in the column you want to standardize (e.g., author).

b. Select **“Edit cells”** > **“Cluster and edit…”**.

   - A dialog box will open, showing clusters of similar values. For example, it might group “Mark Twain” and “Twain, Mark” as potential matches.

c. Use different **clustering methods** (key collision, nearest neighbor, etc.) to identify similar entries.

   - **Key Collision**: Groups based on a phonetic algorithm that ignores small differences.

   - **Nearest Neighbor**: Groups values based on spelling similarity, which is often helpful for misspelled entries.

d. **Review each cluster**: If you agree with OpenRefine’s grouping, type in the standardized name you want to use (e.g., “Mark Twain”) in the **“New Cell Value”** field and click **“Merge and Re-Cluster”** or **Merge and Close** if you are finished with all of the different algorithms you are interested in applying.

### Group Names Back Together with Semicolons

a. **Select the Creator Column**:
   - In the column menu for the creator field, click the dropdown menu for the column that contains the individual names you previously split.

b. **Choose “Edit cells” > “Join multi-valued cells…”**:
   - This will combine the separate values into one cell.

c. **Set the Separator**:
   - In the dialog box that appears, enter **`;`** as the separator (the same one used when you split the names).
   - This will concatenate the names with a semicolon between each name.

d. **Click “OK”**:
   - This will apply the transformation and group the names back together in the same cells, separated by semicolons.

{% include alert.html text="That's it! This same process can be repeated on location, subject and any other fields needing standardization" color="light" align="center" %}


