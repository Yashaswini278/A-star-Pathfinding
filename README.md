# A-star-Pathfinding
This task was assigned to me as part of the selection process for the Autonomous Ground Vehicle Research Group software team at IIT Kharagpur.
The task involves a total of six parts.

## Key Learnings
<p> 1. Effect of different heuristic functions of A-star search on path cost and time </p>
<p> 2. Using Priority Queue in Python </p>
<p> 3. Image scaling using Nearest Neighbour Interpolation </p>
<p> 4. OpenCV: opening, closing and saving images, drawing lines on images, extracting b, g, r channels </p>
<p> 5. Numpy: creating n-dimensional arrays </p>

## Challenges and Workarounds
### 1. Converting given image to a "grid"
The first challenge was to convert the given image to a 2D matrix (or grid), on which the search algorithm could be implemented.
I was given the rgb values of the start and end colors, navigable path color and obstacle color. I could find an approach to overcome the challenge after a lot of web searching. 
Using numpy library, I created a matrix of dimensions same as that of the image, with all its elements initialized to 0. Next, I looped through the image and compared the rgb (bgr in opencv) values of the pixels with those of start and end nodes in order to get their respective coordinates (<b>NOTE</b> : I was given a (100px * 100px) image in which 
the start and end nodes were of 1 pixel size). In order to indicate the non-navigable path, I changed those matrix elements to 1, that had the rgb values matching those of the obstacle. 
#### Another Challenge within this Challenge (😅)
After several attempts at trying to make the code work, I realised I had made a fundamental mistake. A row and a column of an image actually represents the Mat[column][row]
element of the 2D matrix

<img width="820" alt="E321BC66-7E69-4FE5-A567-244FFBE402DC" src="https://user-images.githubusercontent.com/77488107/117321408-b76d5080-aeaa-11eb-9c16-0bc7800a3ac7.png">



### 2. Class Node approach 
In order to keep my code object oriented, a node class had to be created to keep the properties of nodes (or pixels) explored or visited. 
However, this approach didn't work even after hours of debugging. I couldn't come up with a solution to prevent it from getting stuck in an infinite loop.
Finally, I decided to move on to another approach. Here, I defined separate functions for A star search, distance calculations, heuristics and for drawing the final path. 

### 3. Problem with resizing
For better visualization of the path, the final image had to be resized. I tried using cv2.resize(), but the output image turned out to be blurry. 
This is when I came across another method for scaling images "<b> Nearest Neighbour Interpolation </b>". It works on the simple principle of replicating pixels of 
an image depending on a given scale factor. A nice picture which illusrates this:
![image](https://user-images.githubusercontent.com/77488107/117323345-6eb69700-aeac-11eb-95b8-b188023db484.png)
<p>Here, the scale factor is 2. I wanted an enlarged (1000px * 1000px) image, so my scale factor was 10.</p>

## Scope for improvement

### 1.Inability to show contrasting result for non-admissible heuristic
A better non-admissible heuristic could be selected to improve on highlighting the difference in outcomes between admissible heuristic and non-admissible heuristic.
### 2. Code compactness
A more compact method of representing the image as a grid could be explored.

## Conclusion
All in all, it was a fun task to do and gave me the opportunity to explore a variety of heuristics for the A star algorithm as well as for the different OpenCV features.
