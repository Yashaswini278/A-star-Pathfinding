# A-star-Pathfinding
This task was assigned to me as part of the selection process for the Autonomous Ground Vehicle Research Group software team at IIT Kharagpur.
The task involves a total of six parts.

## Key Learnings
<p> 1. Impact of different heuristic functions of A-star search on path cost and time </p>
<p> 2. Using Priority Queue in Python </p>
<p> 3. Image scaling using Nearest neighbour interpolation </p>
<p> 4. OpenCV: opening, closing and saving images, drawing lines on images, extracting b, g, r channels </p>
<p> 5. Numpy: n-dimensional arrays creating </p>

## Challenges and Workarounds
### 1. Converting given image to a "grid"
The first challenge I faced was to convert the given image to a 2D matrix (or grid) on which I could implement the search algorithm.
I was given the rgb values of the start color, end color, navigable path color and obstacle color. After a lot of web searching, I came up with an approach to overcome this. 
Using numpy library, I created a matrix of rows and columns same ad that of the image and all it's elements were 0. Next, I looped through the image and compared the rgb 
(bgr in opencv) values of the pixels with those of start and end node in order to get their respective coordinates (<b>NOTE</b> : I was given a (100px * 100px) image in which 
the start and end nodes were of 1 px size) and for the rgb values matching with those of obstacle, i changed that particular matrix element to 1, indicating non-navigable path.
#### Another Challenge within this Challenge (😅)
After several attempts of trying to make the code work, I realised I had made a fundamental mistake. A row and a column of an image is actually represents the Mat[column][row]
element of the 2D matrix

<img width="820" alt="E321BC66-7E69-4FE5-A567-244FFBE402DC" src="https://user-images.githubusercontent.com/77488107/117321408-b76d5080-aeaa-11eb-9c16-0bc7800a3ac7.png">



### 2. Class Node approach 
In order to keep my code object oriented, a node class had to be created to keep properties of nodes(or pixels) explored or visited. 
However, this approach didn't work even after hours of debugging. I couldn't come up with a solution to prevent it from getting stuck in an infinite loop.
Finally, I decided to move on to another approach. Here, I defined seperate A star search, distance, heuristic and draw the path functions. 

### 3. Problem with resizing
For better visualization of the path, the final image needed to be resized. I tried using cv2.resize(), but the output image turned out to be blurry. 
This is when I came across another method for scaling images "<b> Nearest Neighbour Interpolation </b>". It works on the simple principle of replicating pixels of 
an image depening upon a given scale factor. A nice picture which illusrates this is :
![image](https://user-images.githubusercontent.com/77488107/117323345-6eb69700-aeac-11eb-95b8-b188023db484.png)
<p>Here, the scale factor is 2. I wanted an enlarged (1000px * 1000px) image, so my scale factor was 10.</p>

## Scope for improvement

### 1.Inability to show contrasting result for non-admissible heuristic
A better non-admissible heuristic could be selected to better highlight the difference in outcomes between a admissible heuristic and a non-admissible heuristic.
### 2. Code compactness
A more compact method of presenting the image as a grid could be considered.

## Conclusion
All in all, it was a fun task to do and really gave me the opportunity to explore the variety of heuristic for the A star algorithm as well as the different OpenCV features.
