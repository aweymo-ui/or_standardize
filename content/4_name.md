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
     if(value.contains(" "), value.split(" ")[1] + ", " + value.split(" ")[0], value)
     ```

   - This expression checks if there’s a space in the name (indicating "First Last" format) and then splits the name into first and last. It then reorders it as "Last, First."
   - Click **“OK”** to apply the transformation.


d. **Handling Middle Names or Initials**: If you have middle names or initials that need to be preserved, you can use a slightly more advanced expression to handle names with additional components:

    ```
    if(value.contains(" "), value.split(" ")[-1] + ", " + value.split(" ")[0] + " " + value.slice(1,-1).join(" "), value)
    ```

   - This expression keeps the last name at the beginning, followed by the first name and any middle names or initials.