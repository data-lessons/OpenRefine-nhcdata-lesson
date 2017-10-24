---
title: "Working with OpenRefine"
teaching: 15
exercises: 20
questions:
- "How can we bring our data into OpenRefine?"
- "How can we sort and summarize our data?"
- "How can we find and correct errors in our raw data?"
objectives:
- "Create a new OpenRefine project from a CSV file."
- "Recall what facets are and how they are used to sort and summarize data."
- "Recall what clustering is and how it is applied to group and edit typos."
- "Manipulate data using previous steps with undo/redo."
- "Employ drop-downs to split values from one column into multiple columns."
- "Employ drop-downs to remove white spaces from cells."
keypoints:
- "Faceting and clustering approaches can identify errors or outliers in data."
---

# Lesson

## Creating a Project


Start the program. (Double-click on the openrefine.exe file (or google-refine.exe if using an older version). Java services will start on your machine, and OpenRefine will open in your browser).

Launch OpenRefine (see [Getting Started with OpenRefine](http://www.datacarpentry.org/OpenRefine-ecology-lesson/00-getting-started/)).

OpenRefine can import a variety of file types, including tab separated (`tsv`), comma separated (`csv`), Excel (`xls`, `xlsx`), JSON, XML, RDF as XML, Google Spreadsheets. See the [OpenRefine Importers page](https://github.com/OpenRefine/OpenRefine/wiki/Importers) for more information.

In this first step, we'll browse our computer to the sample data file for this lesson. In this case, we modified the `idigbio_rodents` CSV file. Some data in `weight_g`, `length_mm`, are contrived and some spaces have been added to some text fields and these anomalies are in no way related to the original dataset.

If you haven't already, download the data from:  
[https://figshare.com/s/6fe692e2883347b4c15f](https://figshare.com/s/6fe692e2883347b4c15f)

Once OpenRefine is launched in your browser, the left margin has options to `Create Project`, `Open Project`, or `Import Project`. Here we will create a new project:

1. click `Create Project` and select `Get data from` `This Computer`.  
2. Click `Choose Files` and select the file `idigbio_rodents_openrefine.csv`. Click `Open` or double-click on the filename.
3. Click `Next>>` under the browse button to upload the data into OpenRefine.  
4. OpenRefine gives you a preview - a chance to show you it understood the file. If, for example, your file was really tab-delimited, the preview might look strange, you would choose the correct separator in the box shown and click `Update Preview` (bottom left).
5. For Character encoding, select `UTF-8`. In this case, it will insure that your text, no matter what language, is translated properly so that you don't see garbled output like `&Aring;` for Å, for example.
	1. Learn more about [encoding](https://www.w3.org/International/questions/qa-what-is-encoding).
5. If this is the wrong file, click `<<Start Over` (upper left).  
6. If all looks well, click `Create Project>>` (upper right). 

Note that at step 1, you could upload data in a standard form from a web address by selecting `Get data from` `Web Addresses (URLs)`. However, this won't work for all URLs.

## Order Columns

*Easily reorder columns to simplify work*

OpenRefine makes it very simple to organize your columns, in comparison to a spreadsheet program.

Use the scroll bar at the bottom of your screen to have a look across all the fields in this dataset. Let's move the `genus`, `specificEpithet`, and `scientificName` columns to just after `catalogNumber`. Also, move the `decimalLongitude` column to be before `decimalLatitude`.

1. Just to the left of the `All` column header (the very first column), note the drop-down arrow.
2. Click the *down arrow* and choose `Edit columns` > `Re-order``\remove columns`.
3. In the resulting pop-up, scroll down to `genus` and click and hold to drag it up just after `catalogNumber`.
4. Then do the same for `specificEpithet`, dragging it up to just after `genus`, and finish by moving `scientificName` just after `specificEpithet` and `decimalLongitude` column to before `decimalLatitude`.
5. Click `OK` to complete moving the columns. 
6. Note that if you wanted to remove columns, you only need to drag them to the right box in the pop-up.


<!--## Unique Values

*Discover easily if all values in a column are unique, or not.*

In this dataset, the `uuid` column provides a *globally unique identifier* for each row in the dataset. Let's check to make sure there are no duplicates.

1. Click on the *down arrow* in the `uuid` column and choose `Facet` > `Customized facets` > `Duplicates facet`.
2. Note in the left panel, you get a box with two rows labeled `true` and `false` because we're asking, for each value, is it distinct (unique) or not.
3. Click on `true`. What happens?

> ## Solution

> You see two rows and discover that the `uuids` for both rows are the same. (This error has been added to show how to use this feature of OpenRefine). If you scroll to the far right, you will see the correct `uuid` in the `notes` field. You can fix this now, if you note that you can hover over any given box and click `edit`. This will allow you to `copy-and-paste` the correct value into the `uuid` column. (If you skip this step it will not affect the rest of this lesson). 
> {: .solution}
> -->

## Faceting

*Exploring data by applying multiple filters*

OpenRefine supports faceted browsing as a mechanism for

* seeing a big picture of your data, and
* filtering down to just the subset of rows that you want to change in bulk.

Typically, you create a facet on a particular column. The facet summarizes the cells in that column to give you a big picture of that column, and allows you to filter to some subset of rows for which the cells in that column satisfy some constraint. That's a bit abstract, so let's jump into some examples. 

[More on faceting](https://github.com/OpenRefine/OpenRefine/wiki/Faceting)

Here we will use faceting to look for potential errors in data entry in the `scientificName` column.

1. Scroll over to the `scientificName` column.
2. Click the down arrow and choose `Facet` > `Text facet`.
3. In the left panel, you'll now see a box containing every unique value in the `scientificName` column 
along with a number representing how many times that value occurs in the column.
4. Try sorting this facet by name and by count. Do you notice any problems with the data? What are they?
5. Hover the mouse over one of the names in the `Facet` list. You should see that you have an `edit` function available. 
6. You could use this to fix an error immediately, and OpenRefine will ask whether you want to make the same correction to every value it finds like that one. But OpenRefine offers even better ways to find and fix these errors, which we'll use instead. We'll learn about these when we talk about clustering.

> ## Solution
> 
> There will be several near-identical entries in `scientificName`. For example, there is one entry for `Dipodomys agilia` and
> one entry for `Dipodomis agilis`. These are both misspellings of `Dipodomys agilis`. We will see how to correct these 
> misspelled and mistyped entries in a later exercise.  
{: .solution}

> ## Exercise
>
> 1. Using faceting, find out how many years are represented in this dataset.  
>
> 2. Is the column formatted as Number, Date, or Text? How does changing the format change the faceting display?
>
> 3. Which years have the most and least vouchered specimens and how many?
> 
> > ## Solution
> > 
> > 1. For the column `year` do `Facet` > `Text facet`. A box will appear in the left panel showing that there are 70 unique entries in
> > this column.  
> > 2. Try `Edit cells` > `Common transforms` > `To text`, and you will note the `year` values are black and no longer green and the text is left-justified. Now the column `year` is formatted as Text. 
> > You can change the format again by doing `Edit cells` > `Common transforms` > `To number` and see the values are green again and right-justified.
> > Doing `Facet` > `Numeric facet` creates a box in the left panel that shows a histogram of the number of entries per year. Notice that the data is shown as a number, not a date. If you instead transform the column to a date, the 
> > program will assume all entries are on January 1st of the year (yikes!).
> > 3. After creating a facet, click `Sort by count` in the facet box. The year with the most specimens collected (vouchered) is 2007 with 711. The least is 1973 with one. 
> > 
> {: .solution}
{: .challenge}

## Clustering

In OpenRefine, clustering means "finding groups of different values that might be alternative representations of the same thing". For example, the two strings `New York` and `new york` are very likely to refer to the same concept and just have capitalization differences. Likewise, `Gödel` and `Godel` probably refer to the same person. Clustering is a very powerful tool for cleaning datasets which contain misspelled or mistyped entries. OpenRefine has several clustering algorithms built in. Experiment with them, and learn more about these algorithms and how they work. 

1. In the `scientificName` Text Facet we created in the step above, click the `Cluster` button.
2. In the resulting pop-up window, you can change the `Method` and the `Distance Function`. Try different combinations to 
 see what different mergers of values are suggested.
3. Select the `nearest neighbor` method and `levenshtein` distance function. It should identify nine clusters. 
4. Click the `Merge?` box beside the first five, then click `Merge Selected and Recluster` to apply the corrections to the dataset.
4. Try selecting different `Methods` and `Distance Functions` again, to see what new merges are suggested. You may find there are 
 still improvements that can be made, but don't `Merge` again; just `Close` when you're done.  We'll now 
 see other operations that will help us detect and correct the remaining problems, and that have other, more general uses.

Important: If you `Merge` using a different method or distance function, or more times than described in the instructions above, 
your solutions for later exercises will not be the same as shown in those exercise solutions.

[More on clustering](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

## Split


If data in a column needs to be split into multiple columns, and the parts are separated by a common separator (say a comma, or a space), you can use that separator to divide up the pieces into their own columns.


1. Let us suppose we want to split up the terms in the `scientificName` column into separate columns.
2. Click the down arrow at the top of the `scientificName` column. Choose `Edit Column` > `Split into several columns...`
3. In the pop-up, in the `Separator` box, replace the comma with a space.
4. Uncheck the box that says `Remove this column`.
5. Click `OK`. You'll get some new columns called `scientificName 1`, `scientificName 2`, and so on.
6. Notice that in some cases `scientificName 1` and `scientificName 2` are empty, as are `scientificName4` and `scientificName5`. (HINT: Use `Facet` > `Text facet` to help find the problems). Why is this? What do you think we can do to fix this?

> ## Solution
> 
> For example, the entry that has data in `scientificName 2` and `scientificName 3` but not the `scientificName1` column had an extra space at the beginning of the entry. Leading white spaces are very difficult to notice when cleaning data
> manually. This is another advantage of using OpenRefine to clean your data. We'll look at how to 
> fix leading and trailing white spaces in a later exercise. HINT: Why do you think there are now columns `scientificName4` and `scientificName5`?
{: .solution}

> ## Exercise
>
> Try to change the name of the second new column to "specificEpithet". How can you correct the problem you encounter?
> 
> > ## Solution
> > 
> > 1. On the `scientificName 2` column, click the down arrow and then `Edit column` > `Rename this column`. 
> 2. Type `specificEpithet` into the box that appears. A pop-up will appear that says `Another column already named specificEpithet`. This is because there is another column where we've recorded the `specificEpithet` already.
> 3. You can choose another name like `specificEpithet_test` for this column or change the other 
> > `specificEpithet` column to another name like `speciesEpithet_original`.
> {: .solution}
{: .challenge}

## Undo / Redo

It's common while exploring and cleaning a dataset to discover after you've made a change that you really should have done something else first. OpenRefine provides `Undo` and `Redo` operations to make this easy.


1. Click where it says `Undo / Redo` on the left side of the screen. All the changes you have made so far are listed here.
2. Click on the step that you want to go back to, in this case the previous step. The added columns will disappear.
3. Notice that you can still click on the last step and make the columns reappear, and toggle back and forth between these states.
4. Leave the dataset in the state in which the `scientificNames` were clustered, but not yet split.

Important: If you skip this step, your solutions for later exercises will not be the same as shown in those exercise solutions.

## Trim Leading and Trailing Whitespace

Words with spaces at the beginning or end are particularly hard for we humans to tell from strings without, but the blank characters will make a difference to the computer. We usually want to remove these. OpenRefine provides a tool to remove blank characters from the beginning and end of any entries that have them.


1. In the header for the column `scientificName`, choose `Edit cells` > `Common transforms` > `Trim leading and trailing whitespace`.
2. Notice that the `Split` step has now disappeared from the `Undo / Redo` pane on the left and is replaced with a `Text transform on 3 cells`
3. Perform the same `Split` operation on `scientificName` that you undid earlier. Now you should only get three new columns. Why?
4. Challenge. `Facet` > `text facet` on `scientificName2` column. Scroll down the `facet` results to discover the last entry. Why is there a blank cell for `scientificName2` in the second record row? Can you figure out how to fix this?

> ## Solution
> 
> For part 3 above, removing the leading white spaces means that each entry in this column has exactly one space (between the `genus`, species `specific epithet`, and the `infraspecificEpithet` names). Therefore, when you split with space as the separator, you will get only three columns.
> 
> For the Challenge (part 4), you will have discovered 2 consecutive whitespaces in between the `genus` and `specificEpithet` in the original `scientificName` column.  To fix this you will be glad to note that in addition to leading and trailing whitespaces, Open Refine gives you a way to find and fix these too. 
> > 1. First, use `Undo/Re-do` to go back one step to remove the `Split 15000 cell(s) in column scientificName into several columns by separator`.
> > 2. On the `scientificName` column drop-down, select `Edit cells` > `Common transforms` >  select `Collapse consecutive whitespace`.
> > 3. Now you can repeat the `Split` operation on `scientificName` and you will get 3 new columns but no unexpected blanks. You can test this out by `text facet` of each resulting column and reviewing the `facet` values in the left panel.
{: .solution}

Important: `Undo` the splitting step before moving on to the next lesson. If you skip this step, your solutions 
for later exercises will not be the same as shown in those exercise solutions.

