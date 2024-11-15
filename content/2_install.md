---
title: Installing and Importing
nav: Installing and Importing
gallery: true
---

### Install OpenRefine

   a. [**Download OpenRefine**](https://openrefine.org/download){:target="_blank" rel="noopener"}

   b. **Install and launch** OpenRefine following the instructions provided on the site according to your device.

{% include alert.html text="Note: When you launch OpenRefine, it will run in your default web browser but it is actually running locally on your machine, similar to running a Git site in development locally." color="light" align="center" %}

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Load Your CSV File

   a. Select **“Create Project”** on the OpenRefine homepage

   b. Select **“Choose Files”** and select your CSV file from your computer

   c. Select **“Next”** to load the data. OpenRefine will display a preview of the data for you to verify that it looks correct

   d. In the next intermediary screen, adjust character encoding to `UTF-8`, set column separation to CSV, have the `Parse next 1 line as headers` selected and adjust the project name as needed. The `Store Blank Rows`, `Store Blank Cells as Nulls` and `Use Character " to Enclose Cells Containing Column Separators` should be selected by default. These simply ensure data integrity by not erasing null rows and cells and not separating commas within cells, such as `Smith, John`


   e. Then, select **“Create Project”** 


{% include gallery-figure.html img="or_01.gif" alt="Gif image of the OpenRefine interface opening and formatting a CSV file" caption="Initial Import and Formatting Steps" title="Initial Import and Formatting Steps" %}

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
