---
title: Splitting, Clustering and Joining
nav: Splitting, Clustering and Joining
gallery: true
---

<br>

Looking first at the `creator` field, let's use OpenRefine’s clustering feature to identify and merge similar but non-identical values across a large dataset.

### Split the Creator Field into Individual Names

{% include alert.html text="Note: You will only need to do this step  and the final joining step with columns that contain multiple items separated by semi-colons. In this example, correcting the Publisher field would not need this step as it is a single value column." color="light" align="center" %}

a. **Select the dropdown of the Creator Column**

b. **Choose “Edit cells” > “Split multi-valued cells…”**: 
   - Enter `;` as the separator to split each name into its own cell within the same column.
   - This will separate names like “Painter, Charles G.; Simpson, William Ray; Parks, F.P.” into three individual rows for each name.

{% include gallery-figure.html img="or_02.gif" alt="Gif image of the OpenRefine interface splitting named entities into distinct cells" caption="Splitting Multi-Value Cells" title="Splitting Multi-Value Cells" %}

### Formatting

Before we cluster, I'm noticing many of the discrepancies between the author names are due to inconsistent whitespace. To correct these items or adjust for upper / lowercasing inconsistencies you may encounter:

### Lowercasing and Removing Whitespace

a. In the column menu (e.g., location name), choose **“Edit cells”** > **“Transform…”**.

b. **Enter transformations** to standardize formats:

   - To make all entries title case: Enter `value.toTitlecase()`.
   - To make entries lowercase: Enter `value.toLowercase()`.
   - To trim leading or following whitespace: Enter `value.trim()`.

{% include gallery-figure.html img="or_03.gif" alt="Gif of the OpenRefine Interface Trimming Whitespace From Column" caption="Trimming Whitespace From Column" title="Trimming Whitespace From Column" %}

### Clustering

a. Click on the **drop-down menu** in the column you want to standardize (e.g., author).

b. Select **“Edit cells”** > **“Cluster and edit…”**.

   - A dialog box will open, showing clusters of similar values. For example, it might group “Mark Twain” and “Twain, Mark” as potential matches.

c. Use different **clustering methods** discussed in the previous section to identify similar entries.

d. **Review each cluster**: If you agree with OpenRefine’s grouping, type in the standardized name you want to use (e.g., “Mark Twain”) in the **“New Cell Value”** field and click **“Merge and Re-Cluster”** or **Merge and Close** if you are finished with all of the different algorithms you are interested in applying.

{% include gallery-figure.html img="or_05.gif" alt="Gif of the OpenRefine Interface Clustering Entity Variations with Various Algorithms" caption="Clustering Entity Variations with Various Algorithms" title="Clustering Entity Variations with Various Algorithms" %}

### Group Names Back Together with Semicolons

a. **Select the Dropdown of the Column**:

b. **Choose “Edit cells” > “Join multi-valued cells…”**:

c. **Set the Separator**:
   - In the modal that appears, enter **`;`** as the separator (the same one used when you split the names).

d. **Click “OK”**:

{% include gallery-figure.html img="or_06.gif" alt="Gif of the OpenRefine Interface Joining Multi-Valued Cells To Complete This Process" caption="Joining Multi-Valued Cells To Complete This Process" title="Joining Multi-Valued Cells To Complete This Process" %}

{% include alert.html text="That's it! This same process can be repeated on location, subject and any other fields needing standardization" color="light" align="center" %}


