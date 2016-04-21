# Quiz Admin Interface

## Introduction

Suppose we want to develop a quiz feature into our website. Our editors will create a quiz with a number of questions and answers. Each answer is associated with a score (not visible to readers).

The quiz questions will be displayed to the readers one by one. When they have answered all questions, the final score is displayed and they can share it to any social network platforms.


## Submission

* Submit the answers via email.
* You have to use git to commit the codes, but please **do not** push the codes to the public repository.
* Feel free to make any changes on the provided materials to cope with your design.


## Specification

### Phrase 1

#### Description

In this phrase, we want to implement a basic interface in the admin panel for editors to edit the quiz content.

* The quiz interface consists of:
  * An "Add Question" button
  * A "Calculate Possibilities" button
  * Some (more than 1) questions. Each question consists of:
    * A title with the question number, starting from "Question 1"
    * A line of question content
    * Some answers. For simplicity, let's assume we have only four answers: A, B, C, D.
      * Each answer is associated with a score value. The score is an integer ranged from 0 to 10.
    * A "Remove" button. (except the first question)

#### Task
* Implement the `Add Question` functions:
  * When the `Add Question` button is clicked, append a new question at the end.
  * The new question should contain all the contents mentioned in the specification:
    * With empty question content
    * With all answer scores set to 0
  * There's no limit on number of questions in the quiz.

* Implement the `Remove` functions:
  * When the `Remove` button in a question is clicked, that question is removed.
  * Other question titles should change accordingly to fill up the index gap. For example:
    * Suppose there're 3 questions, namely `Question 1`, `Question 2`, and `Question 3`.
    * When `Question 2` is removed, `Question 3` should become the new `Question 2` to fill the index gap.
    * The first question does not have the `Remove` button and cannot be removed.

* Implement the `Calculate Possibilities` functions:
  * When a user takes the quiz, he/she will choose one and only one answer in each of the questions.
  * We assume the user doesn't not leave any blank answers to any questions.
  * We define the total score of the quiz is the sum of scores of the chosen answers.
  * For example:
    * Question 1:
      * A: 3
      * B: 4
      * C: 5
      * D: 6
    * Question 2:
      * A: 0
      * B: 0
      * C: 1
      * D: 2
  * If the user chooses "AA", the total score is 3; if the user chooses "DC", the total score is 7.
  * As you can see, there're many possible values of the total score, and there can be many ways to achieve the same total score.
  * When the `Calculate Possibilities` button is clicked, count how many possible values of the total score.
  * For each possible value, also count how many possible ways to achieve that total score.
  * Output the result using javascript `console.log`.
  * Sample output for the exmaple quiz above:
    * Score = 3, count = 2
    * Score = 4, count = 3
    * Score = 5, count = 4
    * Score = 6, count = 4
    * Score = 7, count = 2
    * Score = 8, count = 1

### Phrase 2

#### Description

In this phrase, we would like to add an extra feature of displaying different questions base on what readers has answered.

For each question, there is an additional "Question Condition" section, which allows editors to set under what conditions this question will be displayed to the readers.

The following conditions are decided:

* Always display this question
* When the reader chose a specific answer in the previous question
  * e.g. If the reader chose "A" in Question 1, then Question 2 will be shown next, otherwise its skipped.
* When the reader has achieved at least X score from the previous questions

#### Task

Write technical details for phrase 2, including:

* Pseudocode for the "Question Condition" feature
* Technical decisions during the implementation, e.g.
  * How to store the information of "Question Condition"
  * How to update the layout according to the types of conditions, e.g.
    * When the "at least X score" is chosen, how to update the view to show a input box for editors to input the score value
    * How to validate the score value is reasonable (e.g. if the highest possible score to get in the first 2 questions is 11, we cannot let editors to set X=12 in question 3)

### Phrase 3

#### Description

Suppose we have also implemented the frontend section of the quiz, and this feature has released to the public for some time.

Our team continue to develop the quiz, adding and tuning the features in order to make it more attractive. Some examples maybe:

* Allow readers to submit feedback after they have done the quiz
* Allow editors to write different copywritings when the readers has achieved different ranges of scores.

Our engineering team continue to develop and deploy the new features. However, there're a few incidents that, after the deployment, the quiz feature is broken.

Upon inspection, we found the major problems as follows:

* When the engineer develops the feature, sometimes it invloves change of  schema (e.g. adding tables for storing the user feedback), or some migration in the data storage
* The engineer finds a large difficulty to ensure a smooth data migration. They need to do a lot of tests before and after the migration.
* The editors feels uncomfortable to test the new features in the testing environment.
  * The environment provides very few sample quizes. Editors think they are too different from the actual quizes.
  * Editors need to do the tests from the beginning every time to make sure everything doesn't break. This costs a lot of time.


#### Task

* Design the workflow to improve the development, testing and deployment processes, including:
  * How to let engineer to confirm the data migration is smooth
  * How to make a concreate testing flow to increase the confidence
  * How to reduce the time needed in testing without sacraficing the confidence

You are free to introduce new tools / services when applicable.

### Phrase 4

#### Description

Suppose after a whole, our quiz feature becomes very popular that there're around 1,000 new registered users per day after taking the quiz.

Currently we have around 30,000 registered users, and daily traffic for the quiz is 500,000 pageviews.

To cope with the popular demand, we have decided to open the quiz interface to the registered users. We allow them to create, edit, read, and share their own quizes using the interface.

We would also want to collect data of the user-generated quizes to keep track of their performance, for example:

* How many readers have taken the quiz
* How long it takes to finish the whole quiz
* How many readers have reshared the quiz

Then we would like to generate reports from those metrics to evaluate the performance.

#### Task

Architect a solution that is able to:

* Allow a large scale of users to edit the quiz
* Allow a large scale of readers to take the quiz
* Allow a large scale of data to be collected from the readers
* Allow the data to be queried efficiently

