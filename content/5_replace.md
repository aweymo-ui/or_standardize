---
title: Find and Replace
nav: Find and Replace
gallery: true
---

<br>

To do simpler actions like finding and replacing a limited set in naming variances like we need to do in the `pubtype` column for this example:

a. **Select the dropdown menu of the `pubtype` column**

b. **Edit cells** > **Transform** 

c. **Enter GREL expression**:

```
if(value == "Master Gardener", "Master Gardener Program Handbook",
if(value == "Pacific Northwest Extension", "Pacific Northwest Extension Publications", value))
```

d. Click **OK** to apply the transformation

### Explanation:

- The expression checks if the cell contains "Master Gardener" and changes it to "Master Gardener Program Handbook."
- If it contains "Pacific Northwest Extension," it will be replaced with "Pacific Northwest Extension Publications."
- Otherwise, the cell value remains unchanged

{% include gallery-figure.html img="or_07.gif" alt="Gif of the OpenRefine Interface Find and Replace Function" caption="Find and Replace Function" title="Find and Replace Function" %}
