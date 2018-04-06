### Swarmathon III (2018) Competition Rules



Final rules will be available on April 8th, 2018.



The goal of NASA Swarmathon competition is to program a swarm of robots to search a square arena to find and collect as many resources as possible in a fixed period of time. The competition rules are described below. Note that the number of robots, the dimensions of the arena, and the length of time of each round are best estimates at this time, but may change before the final competition due to logistical considerations at NASA Kennedy Space Center. The Physical and Virtual competition rules are identical, with the exception that teams in the virtual competition may not modify the contents of the simulation directory of the base code.



New in Swarmathon III is the addition of obstacles. Teams will need to program their robots to navigate around obstructions in the arena. The surface of Mars is varied, and there are a variety of naturally occurring obstacles that robots need to be able to circumvent.

0. Please suggest modifications to these rules by creating a GitHub pull request.

1. Tournament structure



   1.1. There will be five competition rounds: two preliminary, one quarter-final, one semi-final, and one final.



      1.1.1. The preliminary rounds will require 3 robots to search an approximate 15 x 15 meter walled arena for a maximum of 256 resources in each 20-minute preliminary round. A minimum of eight teams whose robots find and collect the most resources during the two preliminary rounds will move on to the quarter-final round.



      1.1.2. The quarter-final round will require 6 robots to search an approximate 22 x 22 meter walled arena for a maximum of 256 resources over a period of 40 minutes. The top four teams whose robots find and collect the most resources during the quarter-final round will move on to the semi-final round.   



      1.1.3. The semi-final round will require 6 robots to search an approximate 22 x 22 meter walled arena for a maximum of 256 resources over a period of 40 minutes. The top two teams whose robots find and collect the most resources during the semi-final round will move on to the final round.



      1.1.4. The quater-finals, semi-finals, and finals will require 6 robots to search an approximate 22 x 22 meter walled arena for a maximum of 256 resources over a period of 40 minutes.



    1.2. Refer to the "Breaking a tie" subsection near the bottom of this document for rules in the case of a tie score during a given round. 



2. Resources



    2.1. Resources are represented by AprilCubes, foam cubes with [AprilTag](https://april.eecs.umich.edu/wiki/index.php/AprilTags) fiducial markers on all six sides. Note that all AprilTags on all sides are identical: every side is adhered with the [AprilTag from the 36h11 family with id=0](https://github.com/BCLab-UNM/SwarmBaseCode-ROS/blob/master/simulation/models/at0/materials/textures/atag-0.png).



    2.2. Each round's resource distribution will be predetermined and will not be disclosed to teams in advance of the competition. 


    2.3. "Collecting a resource" is defined as delivering an AprilCube to the 1 x 1 meter square [collection zone](https://github.com/BCLab-UNM/SwarmBaseCode-ROS/blob/master/simulation/models/collection_disk/materials/textures/collection_disk.png) at the center of the arena. In order to receive credit for the collection at the end of the round, the AprilCube must be touching the collection zone, or both overlapping the collection zone (in its airspace) **and** touching a cube which is counted as a scoring cube. 
    
    2.4. If resources that were previously delivered are accidentally pushed out of the collection zone by other robots during the round, those resources will no longer count toward the total resources collected by a team during a given round. 
    
    2.5. Scoring for each round will only occur at the end of the round, after all robot motion has been stopped.



    2.6. Scoring decisions of official competition judges are final.



    2.7. The initial placement of target cubes will not be inside the collection zone, nor will they be placed within 50 cm of the arena wall.



3. During the competition



   3.1. Teams may not communicate with their robots in any way during the competition. All robot actions must be autonomous, and starting and stopping of autonomous motion must only be initiated by the official competition staff.



   3.2. The robots used for the competition will be physically identical to the 3 robots provided to each team.



   3.3. If robot-robot communication is required, all communication must be done via ROS topics and the ROS master. Robots will not be aware of each other's hostnames or IP addresses.


4. During each round



    4.1. Each team’s code will be uploaded to the robots before the competition. We will use the **master** branch in each repository.



    4.2. At the beginning of each round, each team’s robots will be placed **roughly** 50 cm from the edge of the collection zone with each robot facing in toward the center of the collection zone. Teams should **not** expect a particular placement of robots about the collection zone other than their orientation towards the collection zone, nor should they expect the arena itself to be oriented in any specific direction. 



    4.3. Each robot should be prepared to receive and react to a start signal in the form of the published value ```2``` on the ```/robotName/mode``` topic, as well as a stop signal in the form of the published value ```1``` on the same topic (identical to the autonomous/manual radio button functionality in the GUI).



    4.4. Each robot must publish a string on the `/robotName/status` topic. This string (set to `online` by default in the SwarmBaseCode-ROS code base) should uniquely identify each team so that competition staff can ensure that the correct code is being run. For example, if a UNM team were to compete in the competition, they might publish the string `UNM: Go Lobos!` on the `/robotName/status` topic in order to uniquely identify their code. Teams that are submitting custom Arduino code should prepend a + symbol to their status message. This allows the arena technical team to pay special attention to uploading the custom Ardunio code and restoring the base Ardunio code after the competiton run.


5. Intervention

     5.1. In the Physical Competition, robots that become stuck due to any fault of the arena, or robots that collide with one another and become stuck, will be moved one meter away by robot wranglers at the direction of arena judges. Fault of the arena includes, for example, robots high-centering on April cubes and cowcatchers becoming stuck under the collection zone. The arena judge will make the final decision as to whether the arena is at fault. Robots in an arena may be replaced if it is determined that a robot's hardware has failed. No intervention will occur in the Virtual competition.
     
     5.2. If a robot is stuck on April Cubes for more than 30 seconds, the robot will be moved approximately one meter away and have its heading maintained.

     5.3. Robots that get stuck on arena walls or other robots will be moved approximately one meter away and turned to face away from the object. 
     
     5.4. If the same robot has gotten stuck on or collided with the same object(s) three times within a 1 minute period, the robot will be moved one meter away and turned to face away from the object. A recurrence of persistent collisions by a rover after having been oriented away from the obstacle may result in the rover's motors being switched off. This decision is at the discretion of the arena tech in consultation with the head tech. This is to avoid having the robot wranglers entirely occupied with preventing a rover from colliding repeatedly during the run.
     
     5.5. Each robot must operate at a safe speed in order to avoid damage from collisions with the walls and with other robots. At the discretion of Physical Competition judges, robots that repeatedly crash into walls, obstacles, or each other at high speeds will be removed from the arena for the remainder of the round.
     
     5.6. Before a robot is moved, its red emergency switch will be switched down to prevent the motors from turning and encoders detecting wheel motion. 

     5.7. If a robot fails because of a hardware malfunction, we will replace the robot during the run. These kinds of failures are sometimes as obvious as a wheel coming off, but it is often difficult to distinguish hardware and software failures. We will keep a close eye on all of the robots' network status, node output/status, sensor outputs, and diagnostic outputs. If a robot is behaving very differently from the others, then we will investigate closely from the master laptop. The arena tech in consultation with the lead tech will determine whether it is appropriate to replace a robot.

     5.7.1. If the techs determine that a robot needs to be replaced, the robot will be pulled from the arena and a standby robot will be set in the center at the arena's start position. Each arena will have at least two standby robots. These will be turned on for the entire run but will not have code running. Once the replacement is set at the arena's starting position it will be initialized and your team's code will start to run. We will work trough this process as quickly as possible but it will take some time.

     5.7.2. Robots pulled from arenas for replacement will be taken to a repair trailer where the problem will be diagnosed and repaired by the hardware tech. The robot will be documented and then returned as standby for its original arena. Examples from previous years have included: motor hardware failure, cowcatchers detaching, and gripper hardware failure. 
   
     5.8. In the event of a robot failing to operate correctly due to a software malfunction outside the control of the team, the robot may be moved to a starting location near the collection zone and have its software restarted. The decision to restart a robot lies with the arena tech in consultation with the head tech. Example failures from previous years include the Ublox GPS node crashing. In rare cases, a software failure could require robot replacement. The same procedures for replacement due to physical malfunctions will be followed.


6. Breaking a tie

     6.1. In the event of a tie for 8th place at the end of the preliminary round, for 4th place at the end of the quarter-final round, 2nd place at the end of the semi-final round, or for the winner of the final round, the tied teams will compete head-to-head during a special tie breaker match. For this match, each team's robots and resources will be reset within their respective arenas. The team whose robots find and collect the most resources in 10 minutes will move on to the next round. If teams are still tied at the conclusion of the overtime match, the match will continue in a "sudden death" form, where the first team to score wins. If no team scores within 10 minutes in the sudden death phase neither team will move forward. 
     
     6.2. The head judge will make the final decision on resolving tie breakers.


7. Modifying the SwarmBaseCode-ROS code base


   7.1. Teams participating in the Physical competition are encouraged to modify any parts of the SwarmBaseCode-ROS code base, including adding or deleting ROS packages and adjusting the Gazebo model files to better replicate the capabilities of their physical robots, **with the exception** of `/src/rqt_rover_gui`, which should **not** be modified. You may modify the `/misc/rover_onboard_node_launch.sh` startup script, but **do not** change the name of the script itself. All committed code that is pushed to a team's GitHub repository by the cutoff date will be pulled and run onboard robots during the Physical competition. Additionally teams participating in the virtual compitition may not modify the contents of the simulation directory or the sbridge package.

   7.2. Teams may modify the Arduino code. Loading the Arduino code must be fully automatic and triggered from the `/misc/rover_onboard_node_launch.sh` script. *Arduino code must be stored in a subdirectory of the teams repository called `arduino/swarmie_control/`*, i.e. `Swarmathon-TeamAbbrev/arduino/swarmie_control/` where Swarmathon-TeamAbbrev is your repository name.
   
   7.3. Because custom Arduino code requires extra logistics at the competition we need to know which teams will have modified Ardiono code well before the competition. **Teams planning to modify the Arduino code must notify us at info@nasaswarmathon.com by Feb 10th, 2018.**

   7.4. **The rover status message must be modified to contain with a preceeding "+" symbol. We will reload the stock arduino code after a run where custom arduino code was used.**

   7.5. Teams participating in the Virtual competition are also allowed to modify any parts of the code base, including adding or deleting ROS packages, **with the exception** of `/simulation`, `/src/rqt_rover_gui`, and `/src/gazebo_plugins`, which **may not** be modified.

8. All physical and virtual teams are required to submit tech and outreach reports. Failure to submit a report will mean your team will not be ranked in the competition, and will be ineligible to advance past the preliminary rounds.

9. Head judge discretion

   9.1. The head judge may disqualify a team at any point during the competition at their discretion.
  
   9.2. The head judge may modify these rules due to weather events or unforseen circumstances.
  
   9.3. Competition rounds may be re-run at the discretion of the head judge. 

10. Calibration Values

   We will provide a comma delimited file called KSC.cal to store the calibration values we obtain at KSC in the root of the home directory, i.e. `~/KSC.cal`. The calibration file will be in the following format:

   `min: { -N1, -N2, -N3 }  max: { +N4, +N5, +N6 }` 

   Where N1 through N6 are natural numbers. This is the same format the calibration code produces.  

   Before the competition the UNM tech team will calibrate the rovers and populate the KSC.cal file with the offset values.  

   We will also provide extended calibration data, this is at the request of teams who are writing custom Arduino code. This extended data will be stored in `~/KSC_extended_calibration.csv` and has the following format:

   `mag.X,mag.Y,mag.Z,accel.X,accel.Y,accel.Z,temperature (high
byte),temperature (low byte)`
