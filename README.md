# Automation_With_OpenCV
A program meant to automate the process of wire insulation production using OpenCV and Picture Processing

This program consists of two parts:
The detection of overlaps (the overusage of material) and the detection of any lacks in insulation.For detecting overlaps in the wires I used a function named check_horizontal_line_contours which is explained below:
Parameters:

contours: List of contours obtained from the image.
threshold_degrees: Threshold angle in degrees. If the absolute deviation of the contour's angle from the horizontal axis is greater than this threshold, the contour is considered problematic.
acceptance_threshold: A value between 0 and 1. Contours with deviations less than or equal to (1 - acceptance_threshold) * threshold_degrees are also considered problematic.
Initialization:

problematic_contours: An empty list to store contours that are identified as problematic.
Iterating Over Contours:

For each contour in the list of contours:
If the contour has less than 2 points, it skips to the next iteration (since a line requires at least two points).
It then uses the cv2.fitLine function to fit a line to the contour.
The function returns a vector (vx, vy) parallel to the line and a point (x, y) on the line.
The angle of the line with respect to the horizontal axis is calculated using np.arctan2 and converted to degrees.
Checking Deviation:

The absolute deviation of the angle from the horizontal direction is calculated (deviation).
If the deviation is greater than the specified threshold_degrees, the contour is considered problematic and is added to the problematic_contours list.
If the deviation is within the acceptance threshold, the contour is also considered problematic and added to the list.
Return:

The function returns a list of contours (problematic_contours) that are identified as potentially problematic, meaning they might represent lines deviating from the horizontal direction.
This will stop the production process and saves material that could've been overlooked by human operator

For the second part of this code which is the detection of any lacks in insulation I've used color filtering to detect any shortcomings in the insulation process.The function works as follows:

time module is imported to measure the execution time of the function.
The function takes image_path as an argument, which is the path to the image to be processed.
The image is read using OpenCV's cv2.imread function.
The image is then converted from the BGR color space to the HSV color space using cv2.cvtColor.
A specific range for a certain color in HSV is defined using lower_blue and upper_blue(in this program blue was used as a demonstration).
A mask is created using cv2.inRange to filter out pixels that fall within the specified blue range.
The function checks if there are any blue pixels in the image using cv2.countNonZero.
Depending on the result, it prints whether there is a problem with the wiring insulation or if it is properly insulated.
Finally, it prints the total execution time of the function.

This program is still incomplete due to the clients and my previous company not coming to a conclusion on financial side of the project,if you wish to contact me on the project,collaboration,pull requests or feedbacks feel free to contact me on any social media platform available on home page or my gmail
