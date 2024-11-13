---
title: Introduction
nav: Introduction
gallery: true
---

## Why OpenRefine Over Google Sheets?

<br>

**While Google Sheets can handle basic find-and-replace or manual editing**, OpenRefine offers specialized features for bulk data cleaning and transformation:

- **Clustering Algorithms**: OpenRefine uses algorithms to automatically group similar entries that might be misspelled or inconsistently formatted, allowing you to merge them efficiently.

- **Scripted Transformations with GREL**: You can write expressions in GREL to transform text in powerful ways that are not available in Google Sheets.

- **Faceting**: Facets allow you to view subsets of your data based on specific characteristics. For example, you can filter a column to only show rows with a particular keyword, which helps locate inconsistencies.

These features make OpenRefine ideal for cleaning up data quickly and accurately, especially in large datasets where doing this manually would be time-consuming.

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

## How Clustering Algorithms in OpenRefine Work

<br>

**Clustering algorithms in OpenRefine identify groups of values that are similar but not identical**. They rely on techniques that analyze the similarity or distance between different strings, grouping values that meet certain similarity criteria. OpenRefine then allows you to merge these grouped values into a standardized form.

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
    - **Metaphone** and **Double Metaphone**: These algorithms convert words into codes based on how they sound. For example, "Smith" and "Smyth" might be converted into the same phonetic code.
    - Soundex: This groups words with similar sounds. It’s helpful for catching misspellings that still sound correct, though it’s less precise with non-English words.

#### When to Use Key Collision

**Key Collision works well for fields where phonetic similarities matter**, like personal names or locations with alternate spellings (e.g., "New York City" and "N.Y.C.").

<div class="symbol-container">
    <p class="symbol">&#10042;</p>
</div>

<br>

### Nearest Neighbor

<br>

The *Nearest Neighbor* method uses a "distance" measure to find strings that are spelled similarly. It’s based on edit distance, meaning it looks at the number of changes needed to transform one string into another.

#### Nearest Neighbor Algorithms

- **Levenshtein Distance**: Measures the number of single-character edits (insertions, deletions, or substitutions) required to change one string into another. For example, "color" and "colour" have a small Levenshtein distance because only one letter differs.
- **Jaccard Similarity**: Compares the similarity between two sets of characters or words. It’s often used to find matches when there’s a high probability of extra or missing words.
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

#### Combining Algorithms

OpenRefine lets you re-cluster data after merging. For example:

1. You can start with a broad Key Collision method, merging general clusters.
2. Then, apply a Nearest Neighbor method for a more fine-grained cleanup.

#### Example of Using Clustering in OpenRefine

1. Suppose you have a column with author names like “Mark Twain,” “Twain, Mark,” “Mark Twian,” and “M. Twain.”
2. Using the Key Collision clustering method:
    - OpenRefine might group “Mark Twain” and “Twain, Mark” because they sound alike or share a similar fingerprint.
3. Then, using the Nearest Neighbor method:
    - OpenRefine might identify “Mark Twian” as a close match to “Mark Twain” because the edit distance is small.

After clustering, you can choose a standardized format (e.g., “Mark Twain”) and apply it across all grouped entries.

