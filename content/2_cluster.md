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

   d. In the next intermediary screen, adjust character encoding to `UTF-8`, set column separation to CSV, have the `Parse next 1 line as headers` selected and adjust the project name as needed. The `Store Blank Rows`, `Store Blank Cells as Nulls` and `Use Character " to Enclose Cells Containing Column Separators` should be selected by default. These simply ensure data integrity by not erasing null rows and cells and not separating commas within cells, such as ```Smith, John```


   e. Click **“Create Project”** to import the data fully.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>


### Standardization Example

To use a practical example for this tutorial, I'll be using metadata for digital collection of different scholarly publications that needs standardizing. Actions needed:

- In the `creator` field, author names need to be standardized and then these names need "last name, first name (or first initial)" formatting
- In the `pubtype` field, "Master Gardener" needs to change to "Master Gardener Program Handbook" and "Pacific Northwest Extension" changes to "Pacific Northwest Extension Publications"
- `Subjects` field needs to be standardized and verified as Getty standards (CDIL follows Getty, SPECS follows LCHS... might want to sort that out at some point)
- `Publisher` field needs basic standardization

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Cluster and Standardize Data

Looking first at the creator field, let's use OpenRefine’s clustering feature to identify and merge similar but non-identical values across a large dataset.

#### Split the Creator Field into Individual Names

a. **Select the Creator Column**: In the column menu for the creator field, click the dropdown.

b. **Choose “Edit cells” > “Split multi-valued cells…”**: 
   - Enter `;` as the separator to split each name into its own cell within the same column.
   - This will separate names like “Painter, Charles G.; Simpson, William Ray; Parks, F.P.” into three individual rows for each name.

#### Formatting

Before we cluster, I am noticing that many of the discrepancies between the author names are due to inconsistent whitespace. To correct these items or adjust for upper / lowercasing inconsistencies:

### Lowercasing and Removing Whitespace

a. In the column menu (e.g., location name), choose **“Edit cells”** > **“Transform…”**.

b. **Enter transformations** in GREL (General Refine Expression Language) to standardize formats:

   - To make all entries title case (capitalizing each word): Use `value.toTitlecase()`.
   - To make entries lowercase: Use `value.toLowercase()`.
   - To trim extra whitespace: Use `value.trim()`.

#### Clustering

a. Click on the **drop-down menu** in the column you want to standardize (e.g., author).

b. Select **“Edit cells”** > **“Cluster and edit…”**.

   - A dialog box will open, showing clusters of similar values. For example, it might group “Mark Twain” and “Twain, Mark” as potential matches.

c. Use different **clustering methods** (key collision, nearest neighbor, etc.) to identify similar entries.

   - **Key Collision**: Groups based on a phonetic algorithm that ignores small differences.

   - **Nearest Neighbor**: Groups values based on spelling similarity, which is often helpful for misspelled entries.

#### Merge Back into original cell format

a. **Review each cluster**: If you agree with OpenRefine’s grouping, type in the standardized name you want to use (e.g., “Mark Twain”) in the **“New Cell Value”** field and click **“Merge and Re-Cluster”**.

