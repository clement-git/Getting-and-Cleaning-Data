---
title: "README.md"
output: html_document
---
## This repo explains how all of the scripts in the file run_analysis.R work and how they are connected.  

### Project data information:
The data linked to this project represents data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 

Here are the data for the project: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

## How the scripts work and are connected:

* Extract the source folder "UCI HAR Dataset" from the zipped source file ( https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip ) into a folder on your local drive, example C:\Users\yourname\Documents

* Set the source folder "UCI HAR Dataset" as your working directory in r studio, example: setwd("C:/Users/yourname/Documents/R/UCI HAR Dataset") 

* Put run_analysis.R into the source folder "UCI HAR Dataset", example
C:\Users\yourname\Documents\R\UCI HAR Dataset


* Running the file ("run_analysis.R") in r studion will read the source dataset, tidy it up and write these files:

merged_cleaned_data.txt (a 10299x68 data frame)

tidy_data_set_with_averages.txt (a 180x68 data frame)

* In r studio Use data <- read.table("tidy_data_set_with_averages.txt") to read the data. Use dim(read.table("tidy_data_set_with_averages.txt")) to check the dimensions of tidy_data_set_with_averages.txt. It is 180x68 because there are 30 subjects and 6 activities; "for each activity and each subject" 30 * 6 = 180 rows. 
