This file explains how the run_analysis.R script works.
Initially we put all the files from the train and test sub-directory needed 
for the project in to the UCIHAR directory. Subject_test, Subject_train,
X_test, X-train, Y_test, Y_train were all copied in to the same directory. 
Features.txt and Features_info were also copied in to the same directory. 
This was the working directory in which the R scripting was done. 
Now I will explain the various commands in the script. 
Command in line 1 reads the features.txt in to R. 
Command in line2 cleans up the names by removing _ and () and leaving behind 
only alphanumeric characters.  The next command changes some of the names in 
features which have BobyBody* to body.
The commmands in the next two lines read the X-train and X_test text files. 
Then they are combined using the rbind command. 
Then we import the plyr and dplyr libraries. 
We change Features3 to horizontal format by doing features3<-t(features3)
On datatable X we give names using features3. 
We create an index of duplicated names and call it x2. 
The next line removes those columns with duplicate names and creates table x3. 
From x3 we remove the columns ending with meanFreq and create table x4.
From x4 we select the columns containing mean and call it x5.
From x4 we select the columns containing std (standard deviation) and call it x6.
We create table x7 by column binding x5 and x6.
The next 3 lines read the y_train and y_test text files and combine them using 
rbind to create column y. 
Similarly the subsequent 3 lines read subject_train and subject_test files and
combine them by rbind and form column s.
WE give column names to s and y in the next two lines. 
We combine x7, s and y to form table b2. 
From b2 we group by subject_id and activity_id and summarise_each (obtain mean)
for each subject and each activity_id. 
We make the column activity_id to be a factor and then substitute the 
activity_id (number)with the activity as characters using revalue 
command. 
Finally we write table b5 to output.txt using write.table command. 