---
title: Introduction
nav: Introduction
gallery: true
---

## Why OpenRefine Over Google Sheets?

<br>

**While Google Sheets and Microsoft Excel can handle both basic functions and complicated equations**, OpenRefine is excellent at bulk data cleaning and transformation, making time consuming language standardization work more efficient through these functionalities:

- **Clustering Algorithms**: Algorithms which group similar entries that might be misspelled or inconsistently formatted, allowing you to split, merge and join multi-value cells.

- **Scripted Transformations with GREL**: General Refine Expression Language allows you to transform text in ways that are often more succinct and customizable than using equations on Sheets or Excel.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

## How Clustering Algorithms in OpenRefine Work

<br>

**Clustering algorithms in OpenRefine identify groups of values that are similar but not identical**, analyzing the likeness or distance between different strings and grouping values that meet certain similarity criteria. OpenRefine then allows you to merge these grouped values into a standardized form.

Here are the main clustering methods and their underlying principles:

### Key Collision
The Key Collision method is a phonetic algorithm that groups values based on a shared "key." It essentially tries to ignore minor differences between similar words and considers how they sound, which makes it useful for names or words with common spelling variations.

#### Key Collision Algorithms

- **Fingerprinting**:
This method is one of the simplest approaches. It:
    - Strips out punctuation and converts all letters to lowercase.
    - Sorts the words alphabetically.
    - Removes duplicates.
    - Creates a "fingerprint" (unique key) from the resulting string.
- For example, "Mark Twain" and "twain, mark" both result in the fingerprint "mark twain," grouping these values together.

- **Phonetic Algorithms**:
    - **Metaphone**: These algorithms convert words into codes based on how they sound. For example, "Smith" and "Smyth" might be converted into the same phonetic code.
    - **Daitch_Moktoff**: This groups words with similar sounds. It’s helpful for catching misspellings that still sound correct, though it’s less precise with non-English words.

#### When to Use Key Collision

**Key Collision works well for fields where phonetic similarities matter**, like personal names or locations with alternate spellings (e.g., "New York City" and "N.Y.C.").

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Nearest Neighbor

The *Nearest Neighbor* method uses a "distance" measure to find strings that are spelled similarly. It’s based on edit distance, meaning it looks at the number of changes needed to transform one string into another.

#### Nearest Neighbor Algorithms

- **Levenshtein Distance**: Measures the number of single-character edits (insertions, deletions, or substitutions) required to change one string into another. For example, "color" and "colour" have a small Levenshtein distance because only one letter differs.
- **PPM (Prediction by Partial Matching)**: Looks at repeated patterns and attempts to predict similarities based on how often parts of the string match.

#### When to Use Nearest Neighbor

Nearest Neighbor is ideal for catching minor typos, misspellings, or small differences in data entries. This is helpful when working with long strings or phrases that might contain small but crucial differences (e.g., “Metropolitan Museum” and “Metropolitan Museum of Art”).

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Choosing Clustering Parameters: Key Collisions vs. Nearest Neighbor

In OpenRefine, you’ll often adjust parameters to determine how strict or lenient the clustering is. For example:

- **Distance Threshold (Nearest Neighbor)**: Lowering the threshold makes clustering more lenient, grouping more items together, while a higher threshold makes it stricter, grouping only very close matches.
- **Normalization (Key Collision)**: Options like lowercasing and removing whitespace standardize how values are treated, ensuring that "New York" and "new york" are considered the same.

{% include gallery-figure.html img="or_17.png" alt="OpenRefine Interface Detail of the Radius or Threshold of the Algorithm That You Can Lower to Make More Strict or Raise to Make More Lenient" caption="Detail of the Radius or Threshold of the Algorithm That You Can Lower to Make More Strict or Raise to Make More Lenient" title="Detail of the Radius or Threshold of the Algorithm That You Can Lower to Make More Strict or Raise to Make More Lenient" %}

#### Example of Using Clustering in OpenRefine

1. Suppose you have a column with author names like “Mark Twain,” “Twain, Mark,” “Mark Twian,” and “M. Twain.”
2. Using the Key Collision clustering method:
    - OpenRefine might group “Mark Twain” and “Twain, Mark” because they sound alike or share a similar fingerprint.
3. Then, using the Nearest Neighbor method:
    - OpenRefine might identify “Mark Twian” as a close match to “Mark Twain” because the edit distance is small.


For a in depth explanation of all of the algorithms and how they function, visit OpenRefine's guide [here!](https://openrefine.org/docs/technical-reference/clustering-in-depth){:target="_blank" rel="noopener"}

