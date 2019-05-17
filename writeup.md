## Model Documentation:


The first thing  I do for path planning, is to figure out if there is a car ahead of me, and what lane that car is in.  This is important in if I should slow down, or change lanes.
I do this by looking at the sensor fusion data, and comparing it to my current location.  

If a car is in front of me:
1) I began to slow down.
2) I begin to look at other lanes to see if there is a car in those lanes
3) I switch lanes if I can switch lanes.


After this, I work on path planning. To create my path, I use the spline library(located in spline.h). 
I create a spline using rough coordinates.

The rough coordinates are generated:
1) Using the last 2 waypoints from the previous path(To ensure continuity and a smooth transition between previous and current state).
2) Calculating waypoints 30m, 60m, and 90m ahead.  This uses the current lane as a reference.

From this, I create a spline using the car velocity and how many points I need to generate(I need 50 points in the spline)
For each point in this, I use the spline to find the y coordinate, and add the new point into the waypoint list.


