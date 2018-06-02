BUAN 6356.003  Spring 2017 (Johnston) Project 1: Movie Data (Revised) Due by:   19 Feb 2017 Description: Use the file “movie_data.csv” from the BUAN_6356 area to fit a regression model explaining the gross movie revenue (“gross”)  by the IMDB user rating score (“imdb_score),  the use of color v. black-andwhite image capture (“color”) and the running time of the movie (duration) for those movies where a positive, non-zero value is provided for both the gross revenue and the movie budget (“budget”).  Do not drop any variables from the data frames. Deliverables: 1. The raw data frame     (name: mData) 2. The filtered (subset) data frame   (name: m2Data) 3. The regression model output   (name: m2Data_lm) 



#Movie_db Assignment 1
#Regression Model explaining the gross movie revenue by the imdb_score, the use of color 
#and the total duration of the movie.
myDir<-("C:/data/BUAN6356")
#Set working directory and load the data in the work environment
setwd(myDir)
movie_file<- "movie_data.csv"
mData <- read.csv(file=movie_file,header=TRUE,sep=",")
#To understand what values exist in the database
head(mData)
# Subsetting the Data for non-negative, non-zero values of both the gross column and the movie budget column from the database
m2Data <- subset(mData,mData$gross > 0 & mData$budget >0)
#Running the Regression Model to explain gross revenue of the movie by color,duration and imdbscore of the movie.
m2Data_lm <- lm(gross ~ imdb_score + color + duration, data=m2Data)
summary(m2Data_lm)

#The output shows you the diffent statistical values
