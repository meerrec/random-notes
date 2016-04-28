## Computer science fundamentals 10

If you never feel like the understanding of some basic algorithm, data structure and design pattern is a must-have kwonledge during your work, then I have to doubt that if you are considered as en eligble software engineer. Here I say computer science fundamentals because we software engineer are not considered as computer scientist, so there is no need for us to explore the black magic of a spesific concept or algorithm. Instead, a software engineer do need to know basic principles of Computer science fundamentals, as well as the ways to solve the most common problems in the software development.

[Algorithms in the "Real World"](http://www.cs.cmu.edu/~guyb/realworld.html)


#### Example 1
Your task is to build a system for English listening skill test. Suppose that you have 100 English sentences with the audios, you will let the user to write down the sentence they just heard and then compare the difference between the original sentence and the one submitted but users. What should you do?

- Good 10/10
You know that this is a place to use edit distance, and you write all the implementaion code within 10 mins.

- Average 5/10
You know there is something called edit distance, which is a way of quantifying how dissimilar two strings are. Then goole edit distance, and find the right implementation within 20 mins.

- Poor 0/10
You have no idea where to start

#### Example 2
You are going to add undo/redo feature in a input field in your website.

- Good 10/10
Two stack: undoStack [] and redoStack [].
    - Type a, push a to undoStack, undoStack = [a] and redoStack = [], input = a
    - Type b, push b to undoStack, undoStack = [a, b] and redoStack = [], input = ab
    - Type c, push c to undoStack, undoStack = [a, b, c] and redoStack = [], input = abc
    - Undo, pop from undoStack, push pop result to redoStack, undoStack = [a, b] and redoStack = [c], input = ab
    - Undo, pop from undoStack, push pop result to redoStack, undoStack = [a] and redoStack = [c, b], input = a
    - Redo, pop from redoStack, push pop result to undoStack, undoStack = [a, b] and redoStack = [c], input = ab


- Poor 0/10
You have no idea where to start

## Coding Ability with a spesific language 25

## Problem Solving skill 25

## Mastery in development Tools 5

## Familiarity with software development methodology processes 5

## Learning Ability 20

## Communication 10