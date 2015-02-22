---
title: "Code Book"
output: html_document
---

### The dataset includes the following files:

- 'features_info.txt': Shows information about the variables used on the feature vector.

- 'features.txt': List of all features.

- 'activity_labels.txt': Links the class labels with their activity name.

- 'train/X_train.txt': Training set.

- 'train/y_train.txt': Training labels.

- 'test/X_test.txt': Test set.

- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. 

- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 

- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 

- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

### Notes: 

- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.
- The units used for the accelerations (total and body) are 'g's (gravity of earth -> 9.80665 m/seg2).
- The gyroscope units are rad/seg.

# What the R code (run_analysis.R) does:

The attached R script (run_analysis.R) performs the following to clean up the data:

* 1. Merges the training and test data sets to create one data set. That is: 
    i. It merges train/X_train.txt with test/X_test.txt to create a 10299x561 data frame, with ("Number of Instances: 10299" and "Number of Attributes: 561")
   ii. It merges train/y_train.txt with test/y_test.txt to create a 10299x1 data frame with activity IDs.
  iii. It merges train/subject_train.txt with test/subject_test.txt to create a  10299x1 data frame with subject IDs
   
* 2. Reads features.txt and extracts only those measurements on the mean and standard deviation for each measurement to create a 10299x66 data frame, because only 66 out of 561 attributes are measurements on the mean and standard deviation. Features are normalized and bounded within [-1,1].

* 3. Reads activity_labels.txt and applies descriptive activity names to name the activities in the data set:

       walking

       walkingupstairs

       walkingdownstairs

       sitting

       standing

       laying

* 4. Labels the data set with descriptive names: all feature names (attributes) and activity names are converted to lower case, underscores and brackets () are removed. The script then merges the 10299x66 data frame containing features with the 10299x1 data frames containing activity labels and subject IDs. The result is saved as "merged_cleaned_data.txt", which is a 10299x68 data frame whose first column contains subject IDs, second column contains activity names, and last 66 columns contain measurements. The Subject IDs are integers between 1 and 30 inclusive. The names of the attributes can be checked with the script: names(read.table("merged_cleaned_data.txt"))

* 5. Uses the data set in "merged_cleaned_data.txt" to Create a 2nd, independent tidy data set with the average of each measurement for each activity and each subject. The result is saved as tidy_data_set_with_averages.txt, which is a 180x68 data frame, whose first column contains subject IDs, second column contains activity names, and then remaining columns contain the averages for each of the 66 attributes. There are 30 subjects and 6 activities, and therefore 180 rows in this tidy data set.
