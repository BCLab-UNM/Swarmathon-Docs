## Guide for Setting up Physical Robots

If you have not yet built your robots, please consult our [Assembly Manual](https://github.com/BCLab-UNM/Swarmathon-Robot/tree/master/AssemblyManual) for instructions on doing so.

### 1. Initial Setup

Download the [Swarmathon III Swarmie Disk Image](http://cs.unm.edu/~mfricke/SwarmathonIII/SwarmathonIII_Swarmie_Image_2017-9-6.iso). The image file is 16 GB. Burn the disk image to a USB drive. There are a variety of tools for burning .iso images to USB drives. Windows 10, Linux, and OS X have built in utilities for burning disk images to USB drives. The free and cross platform Etcher tool at http://etcher.io has worked well for us.

Connect the Intel NUC onboard your robot to a keyboard (USB), mouse (USB), and monitor (HDMI). Insert the USB drive with the Swarmie disk image burned to it. You will need to disconnect the Swarmie USB components to connect the mouse, keyboard, and USB drive. Ensure that the robot motors are turned off (the red switch at the back is down), then turn the NUC on.

Your swarmie should boot into a USB menu with the option to Overwrite the swarmie's harddrive with the new Swarmathon III software. If it does not boot to the USB menu restart your computer and hold down F10 when the NUC's BIOS screen is displayed. A menu of boot devices will appear. Select your USB drive as the boot device and hit enter.

Once you are at the Swarmathon III Swarmie Image install menu press enter. 

-WARNING- Continuing will erase the harddrive in the Swarmie and install the new software -WARNING-

Do not run this software on any computer except the NUC on the Swarmie.

You will be asked to confirm that you want to overwrite the harddrive twice. Once you have confirmed that you want to continue a progress bar showing the installation progress will appear. Wait until the installation finished (should take no more than 20 minutes). The rover will automatically shut itself down at the end of the installation.

Remove the USB installation drive and power on your rover. The Swarmie robot will start up. It now has a preconfigured installation of Ubuntu 16.04 (Xerius Xeres), ROS Kinetic Kame, and the Swarmathon base code ready to use. The Swarmie will login automatically to an account named Swarmie. 

The installation from USB will not modify the code running on the Swarmie's arduino board. If you recieved a new robot this year the arduino code has been preinstalled. You will also find a copy of the Swarmathon-Arduino git repository in the home directory of the swarmie user.

If you need to restore your swarmie to its initial software configuration in the future, you can do so with the USB install drive you created. Doing so will erase any modifications you have made on the Swarmie.

### 2. Hostname and Hosts File Configuration

1. Your robot's hostname should be changed so that each robot will be uniquely identified on your LAN. To change your hostname, open a **Terminal** window and enter ```sudo nano /etc/hostname```. Enter the password you set during the OS installation process when prompted.

2. This file should contain one line with the word "ubuntu". Delete "ubuntu" and replace it with your chosen hostname. Any hostname composed of alphanumeric characters will work; be sure to remember your hostname for later use. Use <kbd>Ctrl</kbd> + <kbd>x</kbd> to save your change and exit the editor.

3. From the Bash prompt, enter ```sudo nano /etc/hosts```.

4. The second line of the **hosts** file should read ```127.0.1.1   ubuntu```. Delete "ubuntu" and replace it with the hostname you chose in step 2.

5. At this point, you should also add to the **hosts** file the IP addresses and hostnames of any other machines on your network (including other robots) that you plan to run Swarmathon-ROS on. For example, you would add a machine named "alpha" with an IP address of "192.168.1.2" by inserting ```192.168.1.2   alpha``` at a new line in the **hosts** file.

6. Once all relevant machines have been added, use <kbd>Ctrl</kbd> + <kbd>x</kbd> to save your change and exit the editor.

### 3. Running SwarmBaseCode-ROS on a Swarmie

Disconnect the keyboard, mouse, and monitor from your robot and place it on a large, flat surface. Ensure that the motors are now turned on (the red switch is up), and that the NUC is on. To start the ROS base code on the robot, follow the directions below:

1. Using another Ubuntu machine that is connected to the same WLAN as your robot, and that has the [SwarmaBaseCode-ROS](https://github.com/BCLab-UNM/SwarmBaseCode-ROS) code base cloned and compiled, follow the **hosts** file setup from Section 2 to ensure that your robot's IP address and hostname have been added to your Ubuntu machine's **hosts** file.

2. Open a **Terminal** window, run ```cd ~/path/to/your/repository```, then run ```./run.sh``` to start the Swarmathon-ROS GUI.

3. Open a second **Terminal** window and connect to your robot by running the command ```ssh robotUserName@robotHostName```, where "robotUserName" and "robotHostName" should be replaced by the username and hostname you selected. When prompted, enter your password.

4. Once the SSH session connects, run the command ```cd ~/path/to/your/repository/misc/rover_onboard_node_launch.sh machineHostName```, where "machineHostName" should be replaced by the hostname of the machine you're currently using.

In your Swarmathon-ROS GUI window, you should see the name of your robot appear in the "Rovers:" box on the left side. It may take up to 10 seconds for the robot's name to appear. When you click on the robot's name, you should see it's camera view appear in the GUI window, along with data from the ultrasonic sensors, IMU, and motor encoders.

Observe the robot for several minutes. If everything is working correctly, you should observe the following indicator lights:

1. A solid green light on the camera

2. A rapidly blinking green light on all three ultrasonic sensors

3. A solid green light on the GPS board on the right side of the robot, and possibly a slow blinking red light if the robot is outside and has achieved a GPS lock

4. A very rapidly blinking, near-solid red light on the microcontroller underneath the Intel NUC

You should also test the joystick control of your robot using either a Microsoft Xbox 360 Controller or the <kbd>i</kbd>, <kbd>j</kbd>, <kbd>k</kbd>, and <kbd>l</kbd> keys on your keyboard.

When you are satisfied that the robot is operating correctly as per the specs above, you may shut it down by flipping the red switch down and holding the power button on the NUC for five seconds.

Your robot is now ready for you to use! Please repeat this process for all 3 of your robots.

### 4. Swarmie IMU Calibration

To work well your Swarmie' IMU sensor must be calibrated for your particular location. A [video guide](https://youtu.be/pL4x7UcuZ3A) to calibrating your rover is available. (Note that if you setup your rover using the USB image install you will not need to download the software packages mentioned in that video. Dialup group membership will have been preconfigured as well.)

### 5. Re-Uploading Swarmathon-Arduino Code

If at some point you need to reupload the Swarmathon-Arduino base code to your microcontroller (after calibrating your rover for example), please follow the instructions in the [Swarmathon-Arduino README](https://github.com/BCLab-UNM/Swarmathon-Arduino/blob/master/README.md).

### 6. Swarmie Maintenance

To charge your robots, plug each of your three smart chargers into standard wall outlets, then connect each of your three robots to the smart chargers via the barrel jack at the rear of the robots (to the right of the red power switch). You should see a red light on the smart charger, which indicates a solid connection. Charge the robot until the light on the smart charger turns green, which indicates that the battery is fully charged, then disconnect the charger. Note that fully charging the battery can take up to 12 hours, and the battery manufacturer stipulates that batteries should be attended during charge to mitigate fire risk (see the Safety Guide for more information about battery charging).

Never run your robots unattended, and handle your robots carefully. You may carry them by the cover plate, but avoid jarring them, dropping them, or crashing them at high speeds. Robots should be able to handle a few bumps into each other, but if they bump into a wall or immovable obstacle at high speed (or sometimes even at low speed), they may flip over and will need to be promptly uprighted.

Operate robots at a safe speed. There are no funds available to repair robots that are damaged due to high speed crashes (or falling down stairs, getting wet, etc.) Additionally, when robots move at high speeds, the ultrasounds may not respond fast enough to avoid crashes into walls, and the camera may not be able to detect April Tags.

Robot wheels may become loose and disengage after repeated testing. Although the robots are capable of driving on only three wheels, you should reattach any loose wheel(s) following the wheel installation instructions in the Swarmie Build Guide.

If you encounter any issues with your robots, please contact the Swarmathon team at [Info@NasaSwarmathon.com](Info@NasaSwarmathon.com), or post questions in the Hardware section of the [NASA Swarmathon Q&A Forum](http://nasaswarmathon.com/qa-forum/), and we’ll help you to diagnose and repair the problem.

### 7. Setting up your teams repoitory.

You should already have a repository under the BCLab organisation on GitHub. Please let us know right away if you do not have access or cand find your repository.

A convenient way customise the SwarmBaseCode-ROS repository which still being able to receive important bug fixes is to setup the SwarmBaseCode-ROS repository as a remote. The commands are as follows:

While in your repository run:

```shell
git remote add SwarmBaseCode https://github.com/BCLab-UNM/SwarmBaseCode-ROS.git
```

Your repository is now able to fetch code from the SwarmBaseCode-ROS repository as well as from your team's repository.

To get bug fixes and changes in the base code use the following command:

```shell
git pull SwarmBaseCode
```

There have been a lot of changes in the code since Swarmathon II. If you try to pull the Swarmathon III code into a branch based on the Swarmathon II code you will have a lot of merge conflicts. You may find it easier to create a fresh branch for Swarmathon III and reimplement the functionality from previous years there.

### 8. Changing the default password for your Swarmie account.

As soon as possible change the password for the Swarmie account (that's the one that logged in automatically on boot). The default password is KSC-2018.

To change you password from the shell type: 
```shell
passwd
```

And follow the prompts.

