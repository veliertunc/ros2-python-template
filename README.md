A ROS 2 python package template
=================
Overview
--------
The folders and files should contain the following:

* `config/`: Configuration files.
* `doc/`: All documentation files 
	* `doc/activity`: Activity diagrams
	* `doc/class`: Class diagrams
	* `doc/requirements`: Software requirements specification.
	* `doc/sequence`: Sequence diagrams
	* `doc/use_cases`: Use case diagrams.
* `launch/`: Launch files.
* `map/`: Map files. Ex: PGM files
* `models/`: SDF model files.
* `rviz/`: RVIZ configuration files.
* `script/`: Other Python scripts.
* `urdf/`: URDF descriptions
* `worlds/`: Gazebo world files
* `CHANGELOG.md`: The log of the changes in chronological order
* `CONTRIBUTING.md`: The guidelines for the contributors
* `LICENSE`: The license information of your package and the packages used
* `README.md`: The README file. Change


Usage
--------
Go to *src* folder under your development workspace:

	cd ~/dev_ws/src

Create a ROS 2 package:

	ros2 pkg create --build-type ament_python my_package --license <LICENSE>

Clone this repo:

	git clone https://github.com/veliertunc/ros2-python-template.git

Copy the contents of the cloned repo into your package:

	cp -r ros2-python-template/* my_package/


Add the following dependencies to the **package.xml**:

	<depend>rclpy</depend>

	<exec_depend>ros2launch</exec_depend>


Append the lines *after* the triple dots(...) to the **data_files** in **setup.py** :

	data_files=[
		...
		
		#Include all configuration files. For example : EKF configuration file
		(os.path.join('share', package_name, 'config'), glob(os.path.join('config', '/**/*.yaml'))),
		# Include all launch files.
		(os.path.join('share', package_name, 'launch'), glob(os.path.join('launch', '/**/*launch.[pxy][yma]*'))),
		# Include all map files.
		(os.path.join('share', package_name, 'maps'), glob(os.path.join('maps', '/**/*.pgm'))),
		# Include all SDF model files.
		(os.path.join('share', package_name, 'models'), glob(os.path.join('models', '/**/*.sdf'))),
		# Include all model configuration files.
		(os.path.join('share', package_name, 'models'), glob(os.path.join('models', '/**/*.config'))),
		#Include RVIZ configuration files
		(os.path.join('share', package_name, 'rviz'), glob(os.path.join('rviz', '/**/*.rviz'))),
		# Include custom Python scripts
		(os.path.join('share', package_name, 'script'), glob(os.path.join('script', '/**/*.[pxy][yma]*'))),
		# Include all URDF files.
		(os.path.join('share', package_name, 'urdf'), glob(os.path.join('urdf', '/**/*.urdf'))),
		# Include all world files.
		(os.path.join('share', package_name, 'worlds'), glob(os.path.join('worlds', '/**/*.world'))),

	],

Then, change the **version, description, maintainer, license** information in **package.xml** and **setup.py** files

Lastly, initialize Git, change the branch name, commit the changes & push them to the remote repo (Optional):

	git init
	git branch -M main
	git add .
	git commit -m "Initial commit"
	git remote add origin <REMOTE_REPO_URL>
	git push -u origin main

TODO
--------
- Add TF2 support with example configuration and launch files
- Add robot_localization support with example configuration and launch files
- Add nav2 stack support with example configuration and launch files
- Add example RVIZ configuration and launch files
- Add example Gazebo configuration and launch files


