#Getting and Cleaning Data Course Project
setwd("~/Desktop/R Directory")

x_test <-read.table("./UCI HAR Dataset/test/X_test.txt")
y_test <-read.table("./UCI HAR Dataset/test/y_test.txt")
subject_test <-read.table("./UCI HAR Dataset/test/subject_test.txt")
#x_test has 561 col, 2947 rows
#y_test has 1 col, 2947 rows, as described in README.txt, y is the label, which correspond to activity_labels.txt
#subject_test has 1 col, 2947 rows
---
x_train <-read.table("./UCI HAR Dataset/train/X_train.txt")
y_train <-read.table("./UCI HAR Dataset/train/y_train.txt")
subject_train <-read.table("./UCI HAR Dataset/train/subject_train.txt")
#x_train has 561 col, 7352 rows
#y_train has 1 col, 7352 rows
#subject_train has 1 col, 7352 rows
---
#Step 1: Merging the data
test_merged<- cbind(y_test, subject_test, x_test)
train_merged<- cbind(y_train, subject_train, x_train)
all_merged <- rbind (test_merged, train_merged)
---
#Step 3: Uses descriptive activity names to name the activities in the data set
# I did step 3 before step 2
features <- read.table("./UCI HAR Dataset/features.txt")
#features is the title of each X column
x_dataset <- rbind(x_test, x_train)
#renaming the columns with features
colnames(x_dataset) <- features[,2]

#Step 2: Extracting Mean and Standard Dev
mean_and_std <- grepl("(mean)|(std)", features[,2])
x_mean_and_std <- x_dataset[,mean_and_std]

#Step 4: Add in variable names
#Read activity table
activity <- read.table("./UCI HAR Dataset/activity_labels.txt")
colnames(activity) <- c('act_id', 'act_name')

y_dataset <- rbind(y_test, y_train)
y_dataset[, 1] = activity[y_dataset[, 1], 2]

#bind y_dataset to x_mean_and_std
tidyDataSet <- cbind(y_dataset, x_mean_and_std)

#Step 5: Create a second independent tidy dataset
write.table(tidyDataSet, file="./tidyDataset")
