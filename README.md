# Quiz Admin Interface
A simple interface for editing a quiz.

## Specification
* The quiz interface consists of:
  * A "Add Question" button
  * A "Calculate Possibilities" button
  * Some (more than 1) questions. Each question consists of:
    * A title with the index, starts from "Question 1"
    * A line of question content
    * Some answers. For simplicity, let's assume we have only four answers: A, B, C, D.
      * Each answer is associated with a score value. The score is an integer ranged from 1 to 10.
    * A "Remove" button. (except the first question)

## Task
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
  * Output the result in a popup window using javascript `alert`.
  * Sample output for the exmaple quiz above:
    * Score = 3, count = 2
    * Score = 4, count = 3
    * Score = 5, count = 4
    * Score = 6, count = 4
    * Score = 7, count = 2
    * Score = 8, count = 1

## Constraints
* Time limit is 2 hours.
* We have included three libraries: jQuery, Backbone, underscore. Please **do not** use other third party libraries.
  * However, you can decide whether or not to use these libraries.
* You have to use git to commit the codes, but please **do not** push the codes to the public repository.
* Other than the above contraints, **you have full control to the provided materials**.
  * Feel free to make any changes: edit the HTML, create new files, etc. It's all up to you to design and implement the solution.


## What we look for
* Well-organized, maintainable and readable codes.
* Atomic git commits with clean and meaningful messages.
* Proper separation in logical parts and view rendering parts.
* High performance in manipulating the DOM elements.
* An efficient and clean algorithm for the `Calculate Possibilies` function.
