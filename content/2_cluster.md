---
title: Importing and Clustering
nav: Importing and Clustering
gallery: true
---

### Install OpenRefine

   a. **Download OpenRefine** from [openrefine.org](https://openrefine.org/) for your operating system.

   b. **Install and launch** OpenRefine following the instructions provided on the site.
- OpenRefine will open in your web browser but runs locally on your computer.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Load Your CSV File

   a. Click **“Create Project”** on the OpenRefine homepage.

   b. Click **“Choose Files”** and select your CSV file from your computer.

   c. Press **“Next”** to load the data. OpenRefine will display a preview of the data for you to verify that it looks correct.

   d. Adjust any necessary settings for delimiters or character encoding if OpenRefine doesn’t automatically detect them correctly.

   e. Click **“Create Project”** to import the data fully.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>


### Explore the Columns and Locate Fields for Standardization

a. **Browse through your data columns** to locate the specific columns you want to standardize, like subject, author, and location name.

b. **Note any inconsistencies** in these columns, such as misspellings, case inconsistencies, or alternative names that should be standardized.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Cluster and Standardize Data

OpenRefine’s clustering feature helps to identify and merge similar but non-identical values across a large dataset.

a. Click on the **drop-down menu** in the column you want to standardize (e.g., author).

b. Select **“Edit cells”** > **“Cluster and edit…”**.

   - A dialog box will open, showing clusters of similar values. For example, it might group “Mark Twain” and “Twain, Mark” as potential matches.

c. Use different **clustering methods** (key collision, nearest neighbor, etc.) to identify similar entries.

   - **Key Collision**: Groups based on a phonetic algorithm that ignores small differences.

   - **Nearest Neighbor**: Groups values based on spelling similarity, which is often helpful for misspelled entries.

d. **Review each cluster**: If you agree with OpenRefine’s grouping, type in the standardized name you want to use (e.g., “Mark Twain”) in the **“New Cell Value”** field and click **“Merge and Re-Cluster”**.

e. **Repeat this process** for each cluster until you’ve standardized all values in the column.
