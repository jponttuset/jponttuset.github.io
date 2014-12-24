---
layout: post
title: Solving Sudoku puzzles like a pro (part I) 
description: "Tutorial to build an augmented-reality real-time Sudoku puzzle solver in C++ using opencv."
comments: true
---


In the following tutorials I'll explain how to solve Sudoku puzzles using C++ and opencv. We'll build a program that captures the webcam video, looks for a Sudoku grid, locates and recognizes the numbers, solves the puzzle, and reprojects the result on the grid (augmented-reality); all in real time. Spoiler alert! Here the final result :)

[![ScreenShot](http://img.youtube.com/vi/OnASlP1SFX0/0.jpg)](https://www.youtube.com/watch?v=OnASlP1SFX0)


This first part will be about locating the grid and numbers. You can download the full code from github, here I'll just highlight the main parts to understand the algorithm. 

######  1. Capture and show the webcam feed
First, let's capture and show the camera feed, the code is pretty self-explanatory.

```C++
/* Create the capture class, '0' means the default webcam */
VideoCapture capture(0);

/* Create the window */
string window_name = "Sudoku AR Solver";
namedWindow(window_name, CV_WINDOW_KEEPRATIO);
    
/* Frame container */
Mat frame;

/* Global loop */
while(true)
{
	/* Capture the frame from the webcam */
	capture >> frame;
	if (frame.empty())
		break;
		
	/* Show the result */
	imshow(window_name, frame);
	
	/* Wait some milliseconds */
	waitKey(5);
}
```

######  2. Detect contours using Canny's edge detector
Coming soon!

######  3. Detect lines using Hough transform
Coming soon!

######  4. Filter lines and recognize the Sudoku grid
Coming soon!

######  5. Extract all 81 Sudoku grid locations
Coming soon!