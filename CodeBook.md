This file describes the variables, the data, and the transformations done in the processing of the data 

# H2 Variables
-  subjectTest - the subject ids for the test data 
-  xTest - the signal data for the test subjects 
-  yTest - the activity number for the test data
-  subjectTrain - the subject ids for the training data
-  xTrain - the signal data for the training subjects 
-  yTrain - the activity number for the training data
-  subjectTestComplete - combines subject Test data into 1 table (subject number, activity type, features) 
-  subjectTrainComplete - combines subject Train data into 1 table (subject number, activity type, features)  
-  testAndTrainComplete - combines Train & Test data into 1 table
-  orderedTestAndTrainComplete - sorted table based on subject#
-  featureNames - feature names to be tidied up and used as column labels
-  activityNames - activity labels
-  tidyNames - list of tidy (more descriptive & syntactically viable) variable names            
-  finalMeanandStandardDeviationData - first tidy dataset with mean and standard deviation data (angle data of weighted means included)
-  secondDataSetWithAverages - final tidy dataset with averages of mean and standard deviation data ordered by subject id
  
# H2 the data
  the data was extracted from various text files containing signal data from the is taken from the accelerometers from the Samsung Galaxy S smartphone. 
  Details of the data can be found at: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
  
# H2 processing procedure
  1. Merges the training and the test sets to create one data set.
    this is done by reading the training and the test sets into the variables: subjectTest, xTest, yTest, subjectTrain, xTrain & yTrain
    and using cbind and rbind, combining them in subjectTestComplete & subjectTrainComplete, and then subsequently into testAndTrainComplete
  2. Extracts only the measurements on the mean and standard deviation for each measurement.
    this is done by assigning finalMeanandStandardDeviationData, which had previously been given descriptive column names, the complete data set subsetted with grep(), searching for key words, such as "mean|deviation|subject|activity"
  3. Uses descriptive activity names to name the activities in the data set
    this was done using replace(). The activity numbers in the table orderedTestAndTrainComplete are reassigned the descriptive names found in activityNames, after some processing (removal of '_' and caps)
  4. Appropriately labels the data set with descriptive variable names.
    this was done by assigning tidyNames with the descriptive names in featureNames, then running through several substitutions using sub() - swapping abbreviations for full words and including some of the descriptions in the features & features.txt and features_info.txt files - (e.g - 't' swapped for 'time.domain.signal.of', use of make.names(), tolower() etc.). 
  5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
    this is done using aggregate() on finalMeanandStandardDeviationData, and assinging the results to secondDataSetWithAverages, which is then written out to smartphone-mean-and-standard-deviation-averages.txt
