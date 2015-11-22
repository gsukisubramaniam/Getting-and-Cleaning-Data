## Code Book: Getting and Cleaning Data::Project
The script run_analysis.Rperforms the 5 steps described in the course project's definition.

#Merging
First, all the similar data is merged using the rbind() function. By similar, we address those files having the same number of columns and referring to the same entities.

#Column Selections
Then, only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given the correct names, taken from features.txt.

#Mutation and Column corrections

As activity data is addressed with values 1:6, we take the activity names and IDs from activity_labels.txt and they are substituted in the dataset.
On the whole dataset, those columns with vague column names are corrected.

##New Dataset

Finally, we generate a new dataset with all the average measures for each subject and activity type (6 activities*30 subjects= 180 rows). The output file is called output.txt, and uploaded to this repository.
Variables
x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
x_data, y_data and subject_data merge the previous datasets to further analysis.
features contains the correct names for the x_data dataset, which are applied to the column names stored in mean_and_std_features, a numeric vector used to extract the desired data.
A similar approach is taken with activity names through the activities variable.
all_data merges x_data, y_data and subject_data in a big dataset.
Finally, "project_output_data" contains the relevant averages which is then stored in "output.txt" file. ddply() from the plyr package is used to apply colMeans() and ease the development.