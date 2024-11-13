---
title: Formatting and Exporting
nav: Formatting and Exporting
gallery: true
---

### Standardizing Author Names to "Last Name, First Name" Format

To transform names like "First Last" into "Last, First" format, you can use General Refine Expression Language (GREL) to split and reorder the names. Here’s a   -by-   guide:

a. **Identify the Author Column**: Select the column where author names are listed.

b. **Create a Text Transformation**:
   - Click on the column dropdown menu.
   - Go to **“Edit cells”** > **“Transform…”**.

c. **Enter the Transformation Expression**:
   - In the GREL transformation box, enter the following code to split and reorder names:
     ```grel
     if(value.contains(" "), value.split(" ")[1] + ", " + value.split(" ")[0], value)
     ```
   - This expression checks if there’s a space in the name (indicating "First Last" format) and then splits the name into first and last. It then reorders it as "Last, First."
   - Click **“OK”** to apply the transformation.

d. **Handling Middle Names or Initials**: If you have middle names or initials that need to be preserved, you can use a slightly more advanced expression to handle names with additional components:
     ```grel
     if(value.contains(" "), value.split(" ")[-1] + ", " + value.split(" ")[0] + " " + value.slice(1,-1).join(" "), value)
     ```
   - This expression keeps the last name at the beginning, followed by the first name and any middle names or initials.

e. **Review and Adjust**: Review the transformed column for accuracy, especially if there are any entries with unusual name formats. You can manually correct any that don’t fit the standard pattern.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Standardizing Subject Names to Getty Standards
For subject names, ensuring compliance with a controlled vocabulary like the Getty Vocabularies (e.g., Art & Architecture Thesaurus, Thesaurus of Geographic Names) typically involves matching each term to its preferred form in the Getty standards. OpenRefine doesn’t natively support direct access to Getty Vocabularies, but you can still standardize names with a few steps:

a. **Import a List of Getty-Compliant Terms (Optional)**:
   - If you have access to a list of Getty-approved terms for your subject field, you can create a CSV or text file with these terms.
   - Import this list into OpenRefine as a new project to use as a reference.

b. **Use Reconciliation Services**:
   - OpenRefine allows you to use reconciliation services to match terms in your dataset to external standards. There are third-party services for various vocabularies, and sometimes institutions make custom reconciliation services available for specific vocabularies.
   - **Add a reconciliation service**: Go to the **Reconciliation** tab in OpenRefine. If you have a URL for a reconciliation service that includes Getty terms, you can add it here. This might require some setup or access permissions.

c. **Match Subject Terms to Getty Standards**:
   - If a reconciliation service isn’t available, you can manually compare your subject names against the Getty list by clustering and editing:
     - **Clustering**: Use **Key Collision** and **Nearest Neighbor** clustering to find variants of the same term (e.g., “Photography” vs. “Photographic Arts”).
     - **Edit to Getty Standard**: For each cluster, standardize the term according to Getty’s preferred term from the reference list.

d. **Create Custom Transformations** (for minor adjustments):
   - If you know certain terms need to be converted (e.g., “Sculpture” should be “Sculpture (visual work)”), you can use **Edit cells** > **Transform…** with GREL expressions like:
     ```grel
     if(value=="Sculpture", "Sculpture (visual work)", value)
     ```
   - Repeat this for any commonly used terms that need to conform to Getty standards.

e. **Manual Adjustments**: Once the bulk of your terms are standardized, review the remaining subject names and manually edit any outliers to match Getty terms.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Lowercasing and Removing Whitespace

a. In the column menu (e.g., location name), choose **“Edit cells”** > **“Transform…”**.

b. **Enter transformations** in GREL (General Refine Expression Language) to standardize formats:

   - To make all entries title case (capitalizing each word): Use `value.toTitlecase()`.
   - To make entries lowercase: Use `value.toLowercase()`.
   - To trim extra whitespace: Use `value.trim()`.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Export the Standardized Data

a. After standardizing both author and subject columns, export your project by going to **Export** > **Comma-separated value (CSV)**.

b. Verify that the standardized data displays correctly in UTF-8 encoding, ensuring consistency and compatibility for CollectionBuilder requirements.