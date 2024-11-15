---
title: Name Formatting
nav: Name Formatting
gallery: true
---

### Remove dates and Unwanted Characters from Name Fields

One item that came up in this example was that some items had birth and death ranges that we needed to remove. While you can find and replace specific punctuation in Google Sheets, random sets of yyyy date ranges is a little trickier. Using OpenRefine, 

- **Select the column with the author names**
- **Select the dropdown menu > `Edit Cells` > `Transform`**
- **Enter the following GREL expression**

```
value.replace(/,\s?\d{4}-?/, "")
```

{% include gallery-figure.html img="or_14.gif" alt="Gif of the OpenRefine Interface Removing Dates and Unwanted Characters from Name Fields" caption="Removing Dates and Unwanted Characters from Name Fields" title="Removing Dates and Unwanted Characters from Name Fields" %}

### Explanation of the Formula

- `value`: Refers to the content of each cell in the column.
- `.replace(...)`: Applies a regular expression to find and replace the birth date portion.
- `/,\s?\d{4}-?/`: This regular expression matches:
  - `,`: A comma
  - `\s?`: An optional space
  - `\d{4}`: Exactly four digits (representing the year)
  - `-?`: An optional hyphen (to account for cases where the year might or might not be followed by a dash)

This formula will remove any pattern like `, 1957-` or `,1957` from the names, leaving just the author's name without the birth date.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Standardizing Author Names to "Last Name, First Name" Format

While the names in the example metadata we are using were already formatted correctly, the following steps will show you how to transform names from "First Last" to "Last, First" format, using General Refine Expression Language (GREL) to split and reorder the names.

a. **Identify the Author Column**: Select the column where author names are listed.

b. **Create a Text Transformation**:
   - Click on the column dropdown menu.
   - Go to **“Edit cells”** > **“Transform…”**.

c. **Enter the Transformation Expression**:

   - In the GREL transformation box, enter the following code to split and reorder names:

     ```
    if(value.split(" ").length() == 3,
   value.split(" ")[2] + " " + value.split(" ")[1] + ", " + value.split(" ")[0],
   value.split(" ")[1] + ", " + value.split(" ")[0]
)
     ```

   - Click **“OK”** to apply the transformation.

{% include gallery-figure.html img="or_15.gif" alt="Gif of the OpenRefine Interface Converting Author Names from First Name Last Name to Last Name, First Name" caption="Converting Author Names from First Name Last Name to Last Name, First Name" title="Converting Author Names from First Name Last Name to Last Name, First Name" %}

1. **`value.split(" ").length() == 3`**: Checks if there are three parts in the name.
2. **For Three-Part Names**: If the name has three parts (e.g., `"first name middle initial last name"`), it reorders to `"last name middle initial, first name"`.
3. **For Two-Part Names**: If there are only two parts (e.g., `"first name last name"`), it reorders to `"last name, first name"`.

