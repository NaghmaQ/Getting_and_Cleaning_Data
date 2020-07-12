# Getting and Cleaning Data Course Project

## Code Book

This project is part of the Course "Getting and Cleaning Data". The ```run_analysis.R``` script performs the tasks of collecting, working with and cleaning a data set.

## Descriptions

### Accessing the downloaded data
Dataset was downloaded and extracted under the folder ```UCI HAR Dataset```. 

- ```features``` variable reads the ```features.txt``` file  
- ```activities``` variable reads the ```activities_labels.txt``` file  
- ```subject_test``` variable reads the ```subject_test.txt``` file  
- ```x_test``` and ```y_test``` variables read the ```X_test.txt``` and ```Y_test.txt``` files respectively  
- ```subject_train``` variable reads the ```subject_train.txt``` file  
- ```x_train``` and ```y_train``` variables read the ```X_train.txt``` and ```y_train.txt``` files respectively  

### Step 1: Merging the training and the test sets to create one data set
The data folder contained two types of data sets - train data and test. Both these data sets were combined to create one data set.

- ```x``` variable stored the combined rows of ```x_test``` and ```x_train```  
- ```subject``` stored the combined rows of ```subject_test``` and ```subject_train```  
- The columns of ```x``` and ```y``` were combined to make a single dataset. This dataset was stored under the variable ```merged_data```  

### Step 2: Extracting only the measurements on the mean and standard deviation for each measurement
The variable ```merged_data``` containing the subject, activity and all feature names was subsetted to include only the subject, activity, and variables that included mean and standard deviation (std). This result was saved as ```tidy_data```.

### Step 3: Using descriptive activity names to name the activities in the data set
The codes for the activities were changed to descriptive activity names.

### Step 4: Appropriately labeling the data set with descriptive variable names
The data set was labeled with descriptive variable names using gsub function. 

- ```code``` column in ```tidy_data``` renamed into ```activities```  
- All ```Acc``` in column’s name replaced by ```Accelerometer```  
- All ```Gyro``` in column’s name replaced by ```Gyroscope```  
- All ```BodyBody``` in column’s name replaced by ```Body```  
- All ```Mag``` in column’s name replaced by ```Magnitude```  
- All variable names starting with character 'f' were replaced by ```Frequency```  
- All variable names starting with character 't' were replaced by ```Time```  

### Step 5: From the data set in step 4, createing a second, independent tidy data set with the average of each variable for each activity and each subject
An independent tidy data set ```tidy_data2``` was created out of the tidy data set obatined from the previous step. This ```tidy_data2``` has the average of each variable for each activity and each subject.

### Creating txt file with write.table() function
A text file named ```Newtidydata.txt``` was created from the data set created in Step 5. The file was created using ```write.table()``` function with ```row.name=FALSE```.


