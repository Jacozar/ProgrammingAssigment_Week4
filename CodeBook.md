# Code Book

This document describes the code inside `run_analysis.R`.

The code is splitted (by comments) in some sections:

* Libraries
* Downloading, loading and merge data
* Manipulating data
* Writing final data to txt file named Tidy_Data.txt


## libraries

The script use the library dplyr that is necessary to run.

### load the 3 files test and free memory
Read the files of test and combine it in one dataframe named Data_Test

Remove the auxiliaries object to free memory

### load the 3 files train and free memory
Read the files of train and combine it in one dataframe named Data_Train
Remove the auxiliaries object to free memory

### merge the dataframes and remove dataframes thats not neccesaries
Merge the dataframes Data_Test and Data_Train in a unique dataframe named Data_All



### load the auxliaries

### loadUciHarData

Loads data, labels and subjects from UCI HAR dataset to a `data.frame`.
The returned `data.frame` contains a column `Activity` with labels integer codes, a column `Subject` with subjects integer codes and all other columns from data.

## Constants

Some fixed values like `dataDir`, `outputDir` and `outputFile` used in the other parts of the code.

## Downloading and loading data

* Downloads the UCI HAR zip file if it doesn't exist
* Reads the activity labels to `activityLabels`
* Reads the column names of data (a.k.a. features) to `features`
* Reads the test `data.frame` to `testData`
* Reads the trainning `data.frame` to `trainningData`

## Manipulating data

* Merges test data and trainning data to `allData`
* Indentifies the mean and std columns (plus Activity and Subject) to `meanAndStdCols`
* Extracts a new `data.frame` (called `meanAndStdData`) with only those columns from `meanAndStdCols`.
* Summarizes `meanAndStdData` calculating the average for each column for each activity/subject pair to `meanAndStdAverages`.
* Transforms the column Activity into a factor.
* Uses `activityLabels` to name levels of Activity factor.

At this point the final data frame `meanAndStdAverages` looks like this:

    > head(meanAndStdAverages[, 1:5], n=3)
      Activity Subject tBodyAcc.mean...X tBodyAcc.mean...Y tBodyAcc.mean...Z
    1  WALKING       1         0.2773308       -0.01738382        -0.1111481
    2  WALKING       2         0.2764266       -0.01859492        -0.1055004
    3  WALKING       3         0.2755675       -0.01717678        -0.1126749


## Writing final data to CSV

Creates the output dir if it doesn't exist and writes `meanAndStdAverages` data frame to the ouputfile.
