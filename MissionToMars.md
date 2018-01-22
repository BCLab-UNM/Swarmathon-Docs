## Entering
The submission deadline is March 27th, 2018. This competition is open to all teams currently taking part in the Swarmathon III competition. There is no requirement that individual students participating in the Mission to Mars competition also contribute to the main Swarmathon competition or vica versa. However, the faculty mentor for students participating in the Mission to Mars competition must also mentor a Swarmathon III main competition team. Virtual and Physical teams are eligible to submit an entry for the Mission to Mars competition.

## Goals
The goal of the NASA Swarmathon Mission to Mars sub-competition is to demonstrate a simulated autonomous robot mission in a Martian environment. The Mission to Mars competition is an additional opportunity for teams to show their work to NASA and to win prize money. The main Swarmathon competition is independent of the Mission to Mars competition.

Teams will be able to show a variety of skills such as graphical design and mission planning in addition to the programming or robots. Teams will be able to develop and demonstrate: modelling and graphical design skills using the Gazebo simulation engine; ideas for autonomous missions that groups of robots can carry out on Mars; and programming skills in coordinating robot tasks. These goals are achieved by teams accomplishing the following tasks:
(1) Specify the task to be performed (examples below).
(2) Model the task environment in Gazebo.
(3) Implement a program that causes a Swarmie robot or robots to carry out the task described in step 1 in the environment defined in step 2.

## Technical skills
Successful teams will show proficiency in programming in the ROS environment, which is becoming a standard in robot control. They will also define 3D robot models and scenery in a physics engine simulation using open source tools such as freecad, Blender and MeshLab or industry tools such as Maya and AutoCad.

## Scoring:
Your team's submission will be graded by NASA engineers at Kennedy Space Center. Deliverables will be submitted using a web form at nasaswarmathon.com. The deliverables are:
(1)	A PDF document containing your mission plan (Max 2 pages, single spaced, 12 point font).
(2)	A link to a youtube video of your mission being executed in Gazebo (max of 6 minutes).
(3)	A link to a GitHub repository that contains your code and simulation.

Each section of your submission will be graded on a 100-point scale, with 100 being the highest possible total:

   A. Mission Plan Text: describe a practical proposed task in detail. (25 points)  
   B. Video: Artistic quality of the video and successful communication of the mission.  At a minimum it should include an export of the simulation.  Narration or subtitles explaining what is happening in the mission would enhance the video. (50 points)  
   C. GitHub Code: The ability of your robots to carry out the mission. (25 points)  


## Rules
The code implementing the mission must use ROS, Gazebo, and the Swarmie robots. There are no restrictions on how many or how few robots are used. <Do you want to allow for the use of other robots.  I think we discussed use of other publically available robots … perhaps we would want to consider existing NASA robots like Pathfinder?> 

The code submitted must be maintained under GitHub. We will create private GitHub repositories for teams who have registered their interest.

## Example Mission Plans:
This example demonstrates the format and scope your mission plan should have.

Mission Goals and Overview
Variations over time in the concentration of water vapour in the atmosphere of Mars is of interest. Gravimetric hygrometers equipped with data loggers can measure atmospheric H20. Six hygrometers are to be deployed around the landing site at locations provided by mission planners. If a hygrometer fails, it is replaced with a backup hygrometer. The lander site has eight hygrometers and three robots. Each hygrometer is labelled with a unique April tag that provides accurate pose information relative to the camera and the unique ID of the hygrometer.

### Example 1
Autonomous hygrometer deployment 
a. Hygrometer target locations are received by the robots. 
b. Robots navigate to the source location of the hygrometers at base camp. 
c. Each robot collects a hygrometer in its gripper. 
d. Each robot navigates to the assigned target location for its hygrometer. 
e. The robot places the hygrometer on the ground. 
f. The robots return to their ready location.
Mission complete.

### Example 2
Malfunctioning Hygrometer Replacement
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

### Questions?
If you have any questions please post on the Q&A Forum at http://nasaswarmathon.com/2018-qa-forum/?p=%3Fforum%3D642017
