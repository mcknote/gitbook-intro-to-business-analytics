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

After understanding the two approaches to find a data, we can further break the selection process of John's score into four steps as follows, to explain how to index and slice a table.

### Table

1. **Find the index** of the row where the "Name" data equals to "John"
2. **Slice the table** using the row index
3. **Find the index** of the column where the header equals to "Score"
4. **Slice the table** using the column index

{% tabs %}
{% tab title="1. Find the index" %}
| Row Index | Name | Score |
| :--- | :--- | :--- |
| **1** | **John** | 100 |
| 2 | Mike | 88 |
| 3 | Ali | 94 |
{% endtab %}

{% tab title="2 - Slide the table" %}
| Name | Score |
| :--- | :--- |
| John | 100 |
{% endtab %}

{% tab title="3. Find the index" %}
| Name | **Score** |
| :--- | :--- |
| John | **100** |
{% endtab %}

{% tab title="4. Slice the table" %}
| Score |
| :--- |
| 100 |
{% endtab %}
{% endtabs %}

We can see that the selection process is basically a deletion process. We focus on the target one dimension at a time, and after two rounds, one for columns and the other one for rows, we can locate the data we were looking for.

It is worth noting that in some packages, the end product from the fourth step is a \(1,1\) table, not the value itself, and would require an extra step to extract the data. But except the difference in data types, this is the standard way to locate a cell in a table - first get the index in one dimension, and that use that index to slice the table.

> **In case you're wondering: Table/Matrix Notation \(r,c\)**
>
> When we refer to the size of a table, we should always present the number of rows first, and then the number of columns. It is a convention from matrix, as the notation directly determines whether certain calculations are available between two matrices. Table adopts this convention.

### List

We can of course apply the same process to select multiple rows or columns. If we want to focus on Mike and Ali's score, either to compare or to calculate the average, I can first find the indexes of their rows, and then slice the table using those indexes.

{% tabs %}
{% tab title="1. Find the index" %}
| Row Index | Name | Score |
| :--- | :--- | :--- |
| 1 | John | 100 |
| **2** | **Mike** | 88 |
| **3** | **Ali** | 94 |
{% endtab %}

{% tab title="2 - Slide the table" %}
| Name | Score |
| :--- | :--- |
| Mike | 88 |
| Ali | 94 |
{% endtab %}

{% tab title="3. Find the index" %}
| Name | **Score** |
| :--- | :--- |
| Mike | **88** |
| Ali | **94** |
{% endtab %}

{% tab title="4. Slice the table" %}
| Score |
| :--- |
| 100 |
| 94 |
{% endtab %}
{% endtabs %}

Again, depending on the data types, the end product we get from step four can be a \(2,1\) table, or a **list** with two elements. List is also a data structure that we can use to store and access data, except unlike table, it is not always two-dimensional; it is usually one-demensional as in this example, or can be nested into multi-dimensional. For now let's focus on the two-element list we got.

The way to index and slice a list is exactly the same as the index approach to our table: we first _find the index_ of the element\(s\), and then _slice the list_ using the index. In the example below, the first two steps are to slice the list using both indexes, and the last two steps using only the first index.

{% tabs %}
{% tab title="1. Find the index" %}
| List Index | Element |
| :--- | :--- |
| **1** | **88** |
| **2** | **94** |
{% endtab %}

{% tab title="2. Slice the list" %}
| Element |
| :--- |
| 88 |
| 94 |
{% endtab %}

{% tab title="3. Find the index" %}
| List Index | Element |
| :--- | :--- |
| **1** | **88** |
| 2 | 94 |
{% endtab %}

{% tab title="4. Slice the list" %}
| Element |
| :--- |
| 88 |
{% endtab %}
{% endtabs %}

We can see from the first two steps that after selecting multiple elements in a list, we will still get a list; while selecting only element will get us the value itself. This is also a way to extract data from the \(1,1\) table object.

> **In case you're wondering: Index in Python and R**
>
> Index system is one of the fundamental differences between R and Python. Launched as a statistical language, R uses natural numbers as its index that starts with 1, while Python, a rather classical programming language, uses [non-negative integers](https://en.wikipedia.org/wiki/Integer_%28computer_science%29) as its index that starts with 0.
>
> So to access the first object in a list, in Python you would use 0 as the index, while in R you would use 1 as the index. We will cover the advanced indexing soon.

