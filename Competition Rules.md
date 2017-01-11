### 2016-2017 NASA Swarmathon Competition Rules

The goal of the NASA Swarmathon competition is to program a swarm of robots to search a square arena and find as many resources as possible in a fixed period of time. The competition rules are described below. Note that the number of robots, the dimensions of the arena, and the length of time of each round are best estimates at this time, but may change before the final competition due to logistical considerations at NASA Kennedy Space Center. The Physical and Virtual competition rules are identical.

- Tournament structure

    - There will be two competition rounds: preliminaries and finals.

    - The preliminary round will require 3 robots to search an approximate 15 x 15 meter walled arena for a maximum of 256 resources over a period of 30 minutes. The arena for the preliminary round will be between 14 and 15 meters square. The exact number and spatial distribution of resources will not be revealed in advance of the competition.

    - The final rounds will require 6 robots to search an approximate 22 x 22 meter walled arena for a maximum of 256 resources over a period of 1 hour. The arena for the final round will be between 21 and 22 meters square.

    - The top four teams whose robots found the most resources during the preliminary rounds will move on to the subsequent round. In the case that multiple teams collect all of the resources, the team that collects them in the shortest time will move on.

- Resources

    - Resources are represented by AprilCubes, foam cubes with [AprilTag](https://april.eecs.umich.edu/wiki/index.php/AprilTags) fiducial markers on all six sides. Note that all AprilTags on all sides are identical: every side is adhered with the [AprilTag from the 36h11 family with id=0](https://github.com/BCLab-UNM/Swarmathon-ROS/blob/master/simulation/models/at0/materials/textures/atag-0.png).

    - Resources will be randomly placed around the arena. Resources may be placed in a uniform distribution, such that the probability of encountering each resource is equal, or in a non-uniform distribution, in which some resources will be grouped together. The resource distribution will selected at random before each round, meaning that neither the exact locations of resources, nor the number of clusters of resources, will not be disclosed to teams in advance of the competition.

    - "Collecting a resource" is defined as delivering an AprilCube to the collection zone at the center of the arena. In order to recieve credit for the collection, the AprilCube must be either inside of the 1 x 1 meter collection zone, or touching the thick black line that designates the edge of the collection zone. If resources that were previously delivered are accidentally pushed out of the collection zone by other robots, those resources will no longer count toward the total resources collected by a team during a given round.

    - Resources will not be placed inside the collection zone, nor will they be placed within 50 cm of the arena wall.

- During the competition

    - Teams may not communicate with their robots in any way during the competition. All robot actions must be autonomous.

    - The robots used for the competition will be physically identical to the 3 robots provided to each team.
    
    - If robot-robot communication is required, all communication must be done via ROS topics and the ROS master. Robots will not be aware of each other's hostnames or IP addresses, but rather only the hostname and IP of the ROS master.

- During each period

    - Each team’s code will be uploaded to the robots before each period.

    - At the beginning of each period, each team’s robots will be placed **roughly** 50 cm from the edge of the collection zone and **roughly** equidistant from one another, with each robot facing in toward the collection zone, then the robots will be turned on. Teams should **not** expect any robot to be placed in any specific position, nor should they expect the arena itself to be oriented in any specific direction.
    
    - Each robot should be prepared to receive a start signal in form of the published value ```2``` on the ```/robotName/mode``` topic, as well as a stop signal in the form of the published value ```1``` on the same topic (identical to the autonomous/manual radio button functionality in the GUI).
    
    - Each robot must publish a string on the `/robotName/status` topic. This string (set to `online` by default in the Swarmathon-ROS code base) should uniquely identify each team so that judges and team members can ensure that the correct code is being run. For example, if a UNM team were to compete in the competition, they might publish the string `UNM: Go Lobos!` on the `/robotName/status` topic in order to uniquely identify their code.

    - Robots that collide with one another in the Physical Competition and become stuck will be separated and placed nearby their original locations by line judges. No intervention will occur in the Virtual competition.

    - Each robot must operate at a safe speed in order to avoid damage from collisions with the walls and with other robots. The maximum allowable velocity for the physical robots is 1.0 m/s linear and 1.0 m/s angular; the maximum velocity for the simulated robots is 1.5 m/s linear and 8.0 cm/s angular (this cap includes the simulated scaling factor). At the discretion of Physical Competition judges, robots that repeatedly crash into walls or each other at high speeds will be removed from the arena for the remainder of the period.

- Modifying the Swarmathon-ROS code base

    - Teams participating in the Physical competition are encouraged to modify any parts of the Swarmathon-ROS code base, including adding ROS packages and adjusting the Gazebo model files to better replicate the capabilities of their physical robots, **with the exception** of `/src/rqt_rover_gui`, which should **not** be modified. You may modify the `/misc/rover_onboard_node_launch.sh` startup script, but please **do not** change the name of the script itself. All committed code that is pushed to a team's GitHub repository by the cutoff date will be pulled and run onboard robots during the Physical competition.
    
    - Teams participating in the Virtual competition are also allowed to modify any parts of the code base, including adding ROS packages, **with the exception** of `/simulation`, `/src/rqt_rover_gui`, and `/src/gazebo_plugins`, which should **not** be modified.
