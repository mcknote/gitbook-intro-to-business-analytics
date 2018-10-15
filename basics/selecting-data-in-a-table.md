---
description: >-
  To interact with the interface, selecting the data to read or write in a table
  is the first step.
---

# Accessing Data In a Table

As promised, one of the biggest benefit to use the table in Excel, or to structure the data, is the ease of accessing the columns, rows and cells in a structured way. Therefore we will spend this whole chapter discussing different ways to select data in a table, mainly _slicing_ and _indexing_. Once we cover this step, data analytics is only a matter of _how_ we are going to change that data.

## Finding the Data through Name or Index

There are two ways of finding the data we want in a table: One is through its column name and row name \(or row condition\), and the other one is through its relative location, or **index**. For example, if we want to find John's score in the table below, the name approach is to filter the row first with the "Name" John and to select the "Score" data; the index approach is to directly select the data in the row 1 and column 2.

**Our score example**

| Name | Score |
| :--- | :--- |
| John | 100 |
| Mike | 88 |
| Ali | 94 |

From the user perspective, it is preferable to use the name approach for its **semantics** advantage, even though the name and the index approaches are usually interchangeable. After all, what we want is _the score of John_, not specific to any row or column index. Therefore, instead of using _B2_ or _row 1 column 2_, we should leverage the column and row names, and have the algorithm figure out the indexes. This was a point in the previous chapter [_What Is a Table?_](what-is-a-table.md).

On the other hand, if we are not looking for specific data, it might be more succinct to just use the indexes. For example, if we want to add 10 points to everyone's score, it doesn't matter if we are selecting John or Ali's score - we just have to add 10 points to each of the selected score. This merit will become more obvious when designing the loop in Python or R. 

For now, just keep in mind that it is better to leverage the existing headers in the table _when necessary_.

## Slicing and Indexing

 If we break the selection of John's score into steps, the process should look like this:

1. **Find the index** of the row where the "Name" data equals to "John"
2. **Slice the table** using the row index
3. **Find the index** of the column where the header equals to "Score"
4. **Slice the table** using the column index

{% tabs %}
{% tab title="1. Find the index" %}
| Row Index | Name | Score |
| :--- | :--- | :--- |
| 1 | John | 100 |
| 2 | Mike | 88 |
| 3 | Ali | 94 |
{% endtab %}

{% tab title="2 - Slide the table" %}

{% endtab %}

{% tab title="3. Find the index" %}

{% endtab %}

{% tab title="Slice the table" %}

{% endtab %}
{% endtabs %}

