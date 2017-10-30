# Swarmathon III (2018) Mission to Mars Sub-Competition


## Notice of Interest

If you wish to enter the competition you let us know by *TBD*. The submission deadline is *TBD*. This competition is open to all teams currently taking part in the Swarmathon III competition. There is no requirement that individual students participating in the Mission to Mars competition also contribute to the main Swarmathon competition or vica versa. However the faculty mentor for students participating in the Mission to Mars competition must also mentor a Swarmathin III main competition team. Virtual and Physical teams are eligable to submit an entry for the Mission to Mars competition.

## Goals
The goal of the **NASA Swarmathon Mission to Mars** sub-competition is demonstrate a simulated autonomous robot mission in 
a Martian environment.  The Mission to Mars competition is an additional opportunity for teams to show their work to NASA and to win prize money. The main competition is independent of the Mission to Mars competition.

Teams will be able to show a variety of skills such as graphical design and mission planning in addition to the programming or robots. Teams will be able to develop and demonstrate modelling and graphical design skills using the Gazebo simulation engine, ideas for autonomous missions that groups of robots can carry out on Mars, and programming skills in coordinating robot tasks. These goals are achieved by teams accomplishing the following tasks:

1. Specify the task to be performed (examples below).
2. Model the task environment in Gazebo.
3. Implement a program that causes a Swarmie robot or robots to carry out the task described in step 1 in the environment defined in step 2.

Technical skills required. Sucessful teams will show proficiency in programming in the ROS environment, which is becoming a standard in robot control. They will also define 3D robot models and scenery in a physics engine simulation using open source tools such as Blender and MeshLab or industry tools such as Maya and AutoCad.

## Evaluation:

Your team's submission will be graded by NASA engineers at Kennedy Space Center. Deliverables will be submitted using a web form at nasaqswarmathon.com. The deliverables are:

1. A **PDF document** containing your mission plan (Max 2 pages, single spaced, 12 point font).
2. A link to a **youtube video** of your mission being executed in Gazebo (max of 6 minutes).
3. A link to a **GitHub repository** that contains your code and simulation.

Your sumbission will be graded on a ten point scale from 1 to 10 with 30 being the highest possible total score using the following criteria:

1) The practicality of the proposed task. Is this a task that could possibly be implemented given robots working together autonomously. The mission does not need to be something that is practical now. Only that it serves a well defined scientific or logistical purpose that could be envisoned for a future mission. Creative missions emplying multiple robots may have an advantage in scoring. 
2) Design and esthetic quality of the Gazebo model as shown in the submitted video (10 points).
3) The ability of your robots to carry out the mission (10 points).

## Rules

The code implementing the mission must use ROS, Gazebo, and the Swarmie robots. There are no restritions on how many or how few robots are used. The code submitted must be maintained under GitHub. We will create private GitHub repositories for teams who have registered their interest.

## Example Mission Plans:

This example demonstrates the format and scope your mission plan should have.

### Mission Goals and Overview

Variations over time in the concentration of water vapour in the atmosphere of Mars is of interest. Gravimetric hygrometers equipped with data loggers are capable of measuring atmospheric H20. Six hygrometers are to be deployed around the landing site at locations provided by mission planners. If a hygrometer fails, it is replaced with a backup hygrometer. The lander site has eight hygrometers and three robots. Each hygrometer is labelled with a unique April tag that provides accurate pose information relative to the camera and the unique id of the hygrometer. 

Autonomous hygrometer deployment
a. Hygrometer target locations are received by the robots.
b. Robots navigate to the source location of the hygrometers at base camp.
c. Each robot collects a hygrometer in its gripper.
d. Each robot navigates to the assigned target location for its hygrometer.
e. The robot places the hygrometer on the ground.
f. The robots return to their ready location.

Mission complete.

### Malfunctioning Hygrometer Replacement
a. The ID of a malfunctioning hygrometer is sent to the robots by mission planners (this ID is encoded by the April tag on the hygrometer).
b. The robots negotiate which of them will retrieve the hygrometer and which of them will transport the replacement.
c. The assigned retrieval robot navigates to the location of the malfunctioning hygrometer.
d. The assigned replacement robot picks up a spare hydrometer from the source location.
e. The retrieval robot picks up the malfunctioning hygrometer in its gripper.
f. The replacement robot transports the spare hygrometer to its target location.
g. The retrieval robot transports the hygrometer to the source location at base camp.
h. The replacement robot places the spare hygrometer down at the target location.
i. The replacement robot navigates to back to the base camp.

Mission complete.
