---
title: Name Formatting
nav: Name Formatting
gallery: true
---

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