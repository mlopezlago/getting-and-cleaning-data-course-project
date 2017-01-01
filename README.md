This repository contains the datafiles and the scripts created to fulfil the requirements for the getting & cleaning data course project.

In it you will find the script run.analysis.R. When run, this script processes the relevant data files found in the UCI HAR Dataset folder, which contains training and test data on the accelerometers from the Samsung Galaxy S smartphone, and generates two tables (in csv files) as per the instructions:

>> the first - mean-and-standard-deviation-data.csv - a table with all the mean and standard deviation data of the various features
>> the second - variable-averages.csv - contains average of each variable for each activity and each subject.

What does the script do?:
first, the txt files containing the data for the training and tests are read and combined into one table and sorted by the subject number. Then, the txt files containing info on the feature & activity names are read in. The numbers corresponding to the activities in original data set are swapped for more descriptive names found in the text file - e.g. 'walking'. The names of the different variables are put through a series of substitutions to make them more readable, by swapping abbreviations for full words and including some of the descriptions in the features & features.txt and features_info.txt files.

The relevant columns (those containing mean and standard deviation data) were then selected and assigned to a new variable, which is then writen out to a csv file. The result is a tidy data set containing 1 column per variable that is descriptively named (as well as sytactically valid), and rows containing each observation.




