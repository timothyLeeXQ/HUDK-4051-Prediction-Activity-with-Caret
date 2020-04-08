# Prediction Activity

This repo contains files for an in-class activity for HUDK 4051: Learning Analytics: Process and Theory. The activity is aimed at familiarising students with caret, which simplifies the process for, and provides a common syntax for creating predictive models in R.

HUDK 4051 is the second of three core courses in the Learning Analytics MS at
Teachers College, Columbia University focusing on the thinking, methods, and
conventions in data science. Particular attention is given to the fields of
Educational Data Mining and Learning Analytics. Refer to the
[Syllabus](https://github.com/timothyLeeXQ/HUDK-4051-Syllabus) (forked from
the [main repo](https://github.com/la-process-and-theory/syllabus) which may
contain updates for future class iterations) for more information on HUDK 4051.

Other classes in the series are:
* [HUDK 4050: Core Methods in Educational Data
Mining](https://github.com/timothyLeeXQ/HUDK-4050-Syllabus)
([Main repo](https://github.com/core-methods-in-edm/syllabus))
* HUDK 5053: Feature Engineering Studio (Starting in May 2020.
 [Main repo](https://github.com/feature-engineering-studio/syllabus))

## Instructor Notes

A mini-prediction competition. Who can produce the best model to predict pass/fail

### Download
* Download the Open University Learning Analytics dataset from [here](https://analyse.kmi.open.ac.uk/open_dataset)
* Import the `studentVle.csv`, `studentAssessment.csv` and `studentInfo.csv` files into R
### Wrangling
* Calculate the average daily number of clicks (site interactions) for each student from the `studentVle` dataset
* Calculate the average assessment score for each student from the `studentAssessment` dataset
* Merge your click and assessment score average values into the the `studentInfo` dataset
### Create a Validation Set
* Split your data into two new datasets, `TRAINING` and `TEST`, by **randomly** selecting 25% of the students for the `TEST` set
### Explore
* Generate summary statistics for the variable `final_result`
* Ensure that the final_result variable is binary (Remove all students who withdrew from a courses and convert all students who recieved distinctions to pass)
* Visualize the distributions of each of the variables for insight
* Visualize relationships between variables for insight
### Model Training
* Install the `caret` package
* You will be allocated one of the following models to test:

  CART (`RPART`), Conditional Inference Trees (`party`), Naive Bayes (`naivebayes`), Logistic Regression (`gpls`)

* Using the `trainControl` command in the `caret` package create a 10-fold cross-validation harness:   
  `control <- trainControl(method="cv", number=10)`
* Using the standard caret syntax fit your model and measure accuracy:  
   `fit <- train(final_result~., data=TRAINING, method=YOUR MODEL, metric="accuracy", trControl=control)`
* Generate a summary of your results and create a visualization of the accuracy scores for your ten trials
* Make any tweaks to your model to try to improve its performance
### Model Testing
* Use the `predict` function to test your model  
  `predictions <- predict(fit, TEST)`
* Generate a confusion matrix for your model test  
  `confusionMatrix(predictions, TEST$final_result)`
