# Code Book

This document describes the code inside `run_analysis.R`.

The code is splitted (by comments) in some sections:

* Libraries
* Downloading, loading and merge data
* Manipulating data
* Writing final data to txt file named Tidy_Data.txt


## libraries

The script use the library dplyr that is necessary to run.

## Downloading, loading and merge data

### load the 3 files test and free memory
Read the files of test and combine it in one dataframe named Data_Test

Remove the auxiliaries object to free memory

### load the 3 files train and free memory
*Read the files of train and combine it in one dataframe named Data_Train
*Remove the auxiliaries object to free memory

### merge the dataframes and remove dataframes thats not neccesaries
*Merge the dataframes Data_Test and Data_Train in a unique dataframe named Data_All
*Remove the dataframe Data_Test and Data_Train to free memory

### load the name_variables
*Load the descriptive names of variables from the file features.txt
*Make a list Names_Variables with the first and second name of the columns: Subject and Activities
*Add to Names_Variables object the rest of the names variables that are in Features object
*Change the names of variables from Data_All to Names_variables
*Extract from dataframe Data_All the columns that I need: Subjetc, Acitivities,and all columns with the strings 'mean()' or 
'std()' to a object named Correc_Columns
*Load the activities_labels file in a object
*Merge the Data_Select and Activities dataframe in one to change the activities number by descriptive activities names

At this point the data set in Data_Select_Tidy is complete Tidy

## Manipulating data
Now group the dataframe Data_Select_Tidy by Activities_Names and Subject and calculate the mean or average of all variables
Load the result in a final dataframe Tidy_Data.txt

At this point the final dataframe `Tidy_Data.txt` looks like this:

    > head(Tidy_Data.txt)
      Activity Subject tBodyAcc.mean...X tBodyAcc.mean...Y tBodyAcc.mean...Z
    1  WALKING       1         0.2773308       -0.01738382        -0.1111481
    2  WALKING       2         0.2764266       -0.01859492        -0.1055004
    3  WALKING       3         0.2755675       -0.01717678        -0.1126749


## Writing final data to txt file

Creates a file Tidy_Data.txt with the final dataframe Data_Seolect_Tidy_Group
