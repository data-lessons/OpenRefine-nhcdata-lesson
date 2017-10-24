# OpenRefine-nhcdata-lesson
OpenRefine lesson for Natural History collection data

### Data set notes.
* This data set is derived from [iDigBio](http://portal.idigbio.org/)  natural science collections specimen data. [This data file](https://figshare.com/s/6fe692e2883347b4c15f) was  modified specifically for use with OpenRefine.
    * Some taxon names have errors introduced.
<!--* One of the Globally Unique Identifiers (in the form of UUIDs) is changed to introduce looking for duplicates in this field.-->
* These modifications were made in order to illustrate some features of Open Refine.
    - Errors were added to the taxon names (`scientificName` field), to demonstrate OpenRefine's ability to find likely mis-entered data.
    - These errors can be found using clustering algorithms on the `scientificName` column, showing the power of the algorithms to find discrepancies quickly and making it simple to fix all issues found.
    
### Options.
* For someone already familiar with OpenRefine, it would be a very simple matter to substitute a different data set, as desired.

