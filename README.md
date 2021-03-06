# Quadcopter Search and Rescue Simulation
### A Final Project for AE483 in Fall 2021
### Charlie Ray, Dennis McCann, Vivek Kodali, Michael Biela

In this project we attempted to showcase a drone's ability to complete search and rescue missions. Drones are ideal for this application because they can reach remote locations that could present a significant challenge for most ground-based transportation methods. We focused on the payload retrieval aspect of search and rescue and chose to explore it by flying a drone to a prescribed location, dropping a ball of putty of some known mass into a cup mounted on the top, and measuring its flight characteristics as it returns to its start location. The results of our experiments are documented here.

## Analysis.ipynb
The analysis notebook is the meat of our project. It includes almost all of the important parts of the project, starting with the theory. All of our theoretical derivations and calculations are completed in Section 2, including setting up the state space model, linear state feedback controller, and linear fixed-gain observer. It then walks through our process for testing the drone featuring videos and plots for each test. Finally we draw a few conclusions at the end and summarize our findings.

## flight.py
This file acts as the drone client. It connects directly to the drone and sends commands on where to move, how quickly to move, how long to remain there, and more. It also controls what data is logged and where that data is stored. While the analysis notebook is important for setting up the autonomous portions of the code, the client is necessary for programming the drone's actual movements.

## data
There are nine files of flight data that we use in our comparisons. They are named using the convention `final_testing{i}_{j}gram.json`, where i corresponds to the number trial that data represents, and j is the amount of mass in grams that the drone picked up. For example, `final_testing2_5gram.json` contains the data from the second trial in which the 5g ball of putty was added to the drone mid-flight. These files contain all the data we chose to log throughout each time step. They start by listing a measurement, say `ae483log.o_x` (which corresponds to the x-coordinate of the drone's position according to our controller/observer). Immediately following this is a list of all the time values this piece of data was recorded, followed then by the data itself. This pattern is repeated for each measurement the client logs.

## videos
The last group of important files in this directory are the videos. We have included three videos that depict one flight test using each sized mass. In these videos you will see the drone lift off and fly to a corner of the room. There it will drop down slightly, simulating the act of landing to retrieve an object from the ground. Instead, the ball of putty is placed in the cup on top and the drone returns to the center position.