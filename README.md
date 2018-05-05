
# Path Planning Project

In this project we output a trajectory to be followed based on the output of sensor fusion component of a Self Driving Car

## Contents

Some of the important files and folders are as follows:

**/src**
- The src folder consists of following important files:
    - main.cpp
        - The main procedure for the program

    - spline.h
        - Header file for the spline library which is used to plot a smooth trajectory thus minimising the jerks experienced by the car
  
**/data**
- The data folder consists of following important files:
    - highway_map.csv
        - Consists of waypoints for the Highway simulation track on which the program is tested

**/Debug**
- This folder consists of the executable file **path_planning.sh**

**Path_Planning.xcodeproj**
- The Xcode IDE file used to build the project
    
**CMakeLists.txt**
- Cmake file to build the project

## Usage
1. Run the **path_planning.sh** file from the terminal/cmd after navigating to the Debug folder so that the file location of the data is correctly interpreted by the program.
2. Run the Udacity's Term 3 simulator and start the simulation.
3. The car will navigate through the traffic successfully.

## Output

The output video is as follows: [Output Video Link](https://youtu.be/owN8G9ZRcdY)

## Observations/ Reflections

1. In the output video we can observe that the car completes the entire lap of 4.32 m without any red warnings or collisions.

2. We have achieved this target by observing the vehicles on the available lanes whenever we wanted to change our lane in order to drive faster and move quicker towards our goal.

3. In the `getOptimumLane()` function in `main.cpp` we have calculated cost for each lane by increasing the cost if there is a vehicle in front of our car or at the back within the safe distance of 30m.

4. As this strategy lead to swift and smooth turns, the distance between the cars is an excellent choice for the cost function.

5. But in real case scenarios we should also consider in which lane our car moves. If we need to make a right turn at the next signal but our function recommends to change our lane to the left side we might end up in the wrong lane.

6. For the current scenario the distance between the cars is the optimum choice as all cars are moving together in the same direction and on a road without any crossroads, entry or exit points.

7. We have used the 'Spline' library to generate a smooth trajectory to navigate. As mentioned in the classroom lectures we have taken sample of points at 30m, 60m and 90m from the car's current position.

8. Using these points we have initialized our spline and then using reference velocity and the spline we create an equally spaced trajectory which maintains all the constraints.

## Conclusions
- The program included in this project can run only in case of straight roads where all the cars are travelling in the same manner.
- If we would like to consider a urban scenario which has 'n' number of intersections and 'm' number of cars travelling in different directions, the program would then be complex.
- In our program we have estimated the 's' parameter of the obstacles at the end of our prediction horizon w.r.t to the obstacle's speed.
- In case of urban scenario the speed of the vehicle won't remain constant due to heavy traffic that the urban scenario would offer and hence the 's' parameter estimation would then be a complex task.
- These complex equations can be fitted accurately with the help of **Machine Learning**.
- At the end we can conclude that the given program can be excellent startup program to guide our vehicle along a highway but not in case of complex road network.
