---
title: "Exporting and Saving Data from OpenRefine"
teaching: 10
exercises: 5
questions:
- "How can we save and export our cleaned data from OpenRefine?"
objectives:
- "Save an OpenRefine project."
- "Export cleaned data from an OpenRefine project."
keypoints:
- "Cleaned data or entire projects can be exported from OpenRefine."
- "Projects can be shared with collaborators, enabling them to see, reproduce and check all data cleaning steps you performed."
---

# Lesson

## Saving and Exporting a Project

In OpenRefine you can save or export the project. This means you're saving the data and all the 
information about the cleaning and data transformation steps you've done. Once you've saved a project, you can
open it up again and be just where you stopped before.

### Saving

By default OpenRefine is saving your project. If you close OpenRefine and open it up again,
you'll see a list of your projects. You can click on any one of them to open it up again.

### Subset Export

Any time you have faceted the dataset, for example, and you have just the rows of interest in your current subset, you can export that subset. Say you found 10 rows with errors, you can then click `Export` > `Comma separated` and you will get a csv file with just those 10 rows in it in your *downloads* folder. Be sure to re-name it meaningfully.

### Exporting

You can also export a project. This is helpful, for instance, if you wanted to send your raw data and cleaning steps to a collaborator, or share this information as a supplement to a publication. 

1. Click the `Export` button in the top right and select `Export project`.
2. A `tar.gz` file will download to your default `Download` directory. The `tar.gz` extension tells you that this is a compressed file.
Which means that this file contains multiple files. You can double-click on the `tar.gz` file and it will expand into a directory. A 
folder icon will now appear. 
3. Look at the files that appear in this folder. What files are here? What information do you think these files contain?

> ## Solution
> You should see:
> - a  `history` folder which contains three `zip` files. Each of these files itself contains a `change.txt` file. 
> These `change.txt` files are the records of each individual transformation that you did to your data. 
> - a `data.zip` file. When expanded, this `zip` file includes a file called `data.txt` which is a copy of your raw data.
> You may also see other files.
{: .solution}

You can import an existing project into OpenRefine by clicking `Open...` in the upper right > `Import Project` and selecting the `tar.gz` 
project file. This project will include all of the raw data and cleaning steps that were part of the original project.

## Exporting Cleaned Data 

You can also export just your cleaned data, rather than the entire project.

1. Click `Export` in the top right and select the file type you want to export the data in. `Tab-separated values` (`tsv`) or `Comma-separated values` (`csv`) would be good choices.
2. That file will be exported to your default `Download` directory. That file can then be opened in a spreadsheet program or imported into programs like R or Python, which we'll be discussing later in our workshop.
3. Rename the file meaningfully and you may want to note all changes made in a separate text file with a matching name pattern. While Open Refine saves your steps, you may want them in plain text rather than as JSON.

Remember from our lesson on Spreadsheets that using widely-supported, non-proprietary file formats like `tsv` or `csv` improves the ability of yourself and others to use your data. 
