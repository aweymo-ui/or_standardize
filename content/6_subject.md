---
title: Formatting and Exporting
nav: Formatting and Exporting
gallery: true
---

<br>

### Reconciliation

OpenRefine has a functionality that *should* allow user's to reconcile data with external databases by matching names, subjects or entities to unique identifiers in those databases, standardizing language to specific schemas such as Getty AAT or LCSH. That said, there are complications due to API compatibility. Because the reconciliation process engages in a transfer of sharing data with the http address of these institutions, connection failures caused by security settings can occur, especially with our technology as an academic institution. 

This is what I encountered trying to reconcile with Getty's databases and Library of Congress doesn't even have a listed service in OpenRefine, likely due to a lack of standardized API endpoints needed for this type of integration. 

{% include gallery-figure.html img="or_11.gif" alt="Gif of the OpenRefine Interface Failing to Connect with the Getty Vocabulary Database" caption="Failing to Connect with the Getty Vocabulary Database" title="Failing to Connect with the Getty Vocabulary Database" %}

That said, I was able to successfully reconcile with other databases that may be useful for standardization, including Geonames for verifying location names, ORCID iD for bibliometric data and Open Library for general subject terms. 

{% include gallery-figure.html img="or_12.gif" alt="Gif of the OpenRefine Interface Successfully Connecting with the Geonames Vocabulary Database" caption="Successfully Connecting with the Geonames Vocabulary Database" title="Successfully Connecting with the Geonames Vocabulary Database" %}

**To reconcile data:**

- Select the column that you would like to reconcile
- Select the dropdown `Reconcile` > `Start Reconciling`
- `Add Standard Service` and enter the http address from the [Reconciliation Service Test Branch](https://reconciliation-api.github.io/testbench/#/)
- This will take you to an intermediary screen where you can select which areas of the database you would like to use, select the level of filtering and maximum number of "candidates" to return for each entity
- After a good deal of processing, the candidates will generate in each of the cells and you have the option to select these options for either just the one entity or to apply them to all of the subjects in that column. 

{% include gallery-figure.html img="or_13.gif" alt="Gif of the OpenRefine Interface Displaying Output of Reconciled Data, Displaying Multiple Candidates Next to Checkbox Options to Adopt Words Either Individually or Across the Field" caption="Output of Reconciled Data, Displaying Multiple Candidates Next to Checkbox Options to Adopt Words Either Individually or Across the Field" title="Output of Reconciled Data, Displaying Multiple Candidates Next to Checkbox Options to Adopt Words Either Individually or Across the Field" %}

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Export the Standardized Data

**FINALLY**

a. After standardizing both author and subject columns, export your project by going to **Export** > **Comma-separated value (CSV)**.

b. Verify that the standardized data displays correctly in UTF-8 encoding, ensuring consistency and compatibility for CollectionBuilder requirements.

{% include gallery-figure.html img="or_16.gif" alt="Gif of the OpenRefine Interface Exporting CSV" caption="Exporting CSV" title="Exporting CSV" %}