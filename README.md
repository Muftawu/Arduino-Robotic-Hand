# Arduino-Robotic-Hand

Hello Karen. This is a simple documentation to explain the code to you.

------------------------------------------------ARDUINO CODE------------------------------------------------ 

![A](https://user-images.githubusercontent.com/84936717/147300910-8181cb4f-868f-4da7-a626-ab1b3d8acbdb.png)
In this part, the servo library is included and we tell the compiler that we will be receiving 
values from the python script through serial communication and each data contains a single digit.

![b](https://user-images.githubusercontent.com/84936717/147301028-57bde2a2-2c74-4509-a1c5-81264d13d163.png)
We declare our servo motor parameter here. As you can see, each finger maps to an individual servo.

![c](https://user-images.githubusercontent.com/84936717/147301092-504a2f7d-c976-40cb-a09c-ff9f4bde9b87.png)
The 'valRec[numOfValRec]' is an array to store our received values. 

For 'int counter = 0; 
We set a variable called counter to check if we pass the maximum number of digits we want to receive from the serial communication.

Also the 'bool counterStart = false;'
This is a boolean to control the behaviour of our servo motor if the counter value is obtained. 

int stringLength = numOfValRec * digitsPerValRec + 1;
String receivedString;
The above two lines tell us the length of the received data/string we want from the serial communication while 
the second line store the received string


![g](https://user-images.githubusercontent.com/84936717/147301351-d2eaa88d-684e-44c2-ae6e-6c2fa679e668.png)
In the setup, we initialize our serial object and set the pinModes of each servo motor.

![m](https://user-images.githubusercontent.com/84936717/147301595-8ce4f8da-2fc0-4268-a351-a8dd8a1889e4.png)
The above function is the main function that receives the serial data and processes it to generate an output.
The output will be passed through series of if statement to execute a specific block of codes if conditions are met.

![t](https://user-images.githubusercontent.com/84936717/147301425-f4e4c651-e073-4c9e-87a1-6ed6dd52bb33.png)
In the loop function, we simply tell the compiler that if we received a data and pass it through the receivedData function above.
if the outcome falls within our if statements, the block of code under that if statement is executed.
So if we receive a 1 as output on say the Ring finger motor, the servo connected to that finger rotates an angle of 180 degrees.




-----------------------------------------------PYTHON CODE----------------------------------------

The python code is fairly simple. On line 1, the computer vision package is imported.
Line 2 import the HandTrackingModule from cvzone and line 3 also imports the Serial Module 
from cvzone.

Incase you do not have the cvzone package, you can install by running the command below
   pip install cvzone
   
 Also 'pip install opencv-python' will install the cv2 package.
 
 On line 5, we initialize our webacam by using the VideoCapture property
 On line 6, we create an instance of the HandTrackingModule called detector
 Line 7 also creates an instance of the SerialModule package
 
 we start our loop on line 9
 On Line 10, we read an image or frame from the webcam called img
 Line 11 uses the findHands property to detect our hands in the img frame
 Line 12, reads the number of hands detected im the frame and determines if its 1. If True, the rest of the code is executed.
 Line 13, uses the fingersUp property to find the fingers that have been raised in the image and creates an array to store the values in a variable called finger
 Line 14, then sends those values over to Arduino through serial communication for processing.
 Line 16 and 17 display our image and set the delay by 1 millisecond. 
 
 

This sums up my explanation. Please let me know if anything need further explanation.

