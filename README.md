one camera knee angle

What is this project?
    This is a gait analysis system that uses only one camera to take a video of a participant gait with markers. The system will try to measure hip knees and ankles angle from the markers in videos. The system is  trained with video and gait data from the Vicon system with machine learning. 

Current state
    Now, the program can only calculate right knee angle. 

What does this program do?
    For the main1 program, this program is built for medical personals, it will try to detect all bright spots in the input video and track them and give those spots a name. After that, the user has to manually identify the spots by matching them with the given set of markers name. The program will automatically print out the coordinate of each marker. After the user satisfies with markers labeling, the program will input the coordinate in math models and show angles. 
    For the main2 program, this program is used to build a dataset.
It will sync knee angle data from the Vicon system with coordinates from thigh, knee and ankle markers. The reason to sync is both systems don't have the same sampling rate and didn't start at the same time. The output data set will have 7 columns, the first 6 will be coordinates, the last one is an angle.
    The main3 is data analysis and modeling program. It can print out the graph from the dataset and train a model. The model can be saved and put in the main1.

About the code
    This program is coded in python. For image and video processing, Open CV is used. The GUI is written with Tkinter lib. Scikit-learn is used for machine learning. Everything is built with Jupyter Notebook.

How to use?
For medical personals
1. Select the video that you want to read the knee angle.  
2. Video can be paused with the pause button. The video needs to be paused to be able to seek.
3. Click on the threshold check button to turn the video in black and white.
4. Adjust the threshold bars until most markers are visible without too much noise.
5. Write markers ID. After the writing is done, the dialog box will pop up. 
6. Seek the video to the point where you want to start, then label the markers with the IDs and click add. You can clear the added pair with the clear button.
7. After done adding markers in the current frame, click set here to start setting the markers.
8. You can reset the set markers at this current frame with the reset here button.
9. The saved markers label can be viewed with the show set button.
10. Click on the calculate angle button to calculate and show the angle in each frame.
11. The output data can be saved in excel and video.

For the operator
To build a dataset
1. In main2, input location of Vicon data excel in CSV, then count row that contains data in excel start from row 1 count as 0 until the header row which should have a word "#Field", put that number in column_label.
Input location of markers coordinates data excel in CSV. The file should have 6 columns contains THIx, THIy, KNEx, KNEy, TIBx, and TIBy in order.
2. Print some data out to check for an error.
3. Input hip angle column by finding hip angle column in excel and divide it by 3, then put X. follow by that rounded number. 
ex. column 50 -> 50/3= 16.6666666667 -> 'X.16'
The knee and ankle angle should be the next value.
ex. hipColumn= 'X.16', kneeColumn = 'X.17',ankleColumn = ankle 'X.18'
4. Print out to check the data.
5. Display a graph for the next step.
6. The hard part, find the frame that matches with Vicon data row(that row-the first data row). For example, the initial contact frame is 257 and the match data is in row 70 and the first row of this data is 14, so an actual frame is 70-14 = 56. So, the frameMatch = 257 and ViconDataIndex = 56.
7. Input camera sampling rate(FPS) and Vicon sampling rate. Please consider that video in slow motion will have more FPS.
8. Run until the last cell, edit your dataset filename and save location to export as CSV excel file.
9. You have done a good job.
To build a model
1. Input train data location and test data location.
2. Input your model filename.
3. Run every whole damn thing.
4. The model should be saved in your code directory.

Credits
Project supervisor1: Prof Dr. YEOW Chen Hua
Project supervisor2: Luis Carlos Hernandez Barraza
Main program constructer: Chavalchart Herabut
Coding advisor1: Santhapon Sripilaipong
Coding advisor2: Kittipos Giatgong
Subject1: Azmall
Sublect2: Nicolas
Advanced Robotics Centre (ARC) NUS
Original soure code
tracking code: https://www.pyimagesearch.com/2018/07/23/simple-object-tracking-with-opencv/ 