# udm_ros_lerobotmarcheur_project
This repo contains the project for RI in Y1S2. Note that each folder (partie_1, partie_2 or partie_3) represents a separate section in the project. It is recommended to move each package to <catkin workspace>/src/ after retrieving this repo. Note that some files require adding permissions or making them executable:
 ```chmod +x <filename>
 ```

## partie_1
### Partie 1 - Conception d’une Jambe
The folder 'partie_1' corresponds to the first part of the project: "Conception d’une Jambe". Additional information on the tp is available in the PDF file.  To run this section of the project, execute the following:
```
mkdir catkin_ws
cd catkin_ws
mkdir src
cd src
git clone https://github.com/azezezaaa/udm_ros_lerobotmarcheur_project  
mv udm_ros_lerobotmarcheur_project/partie_1/* . && rm -rf udm_ros_lerobotmarcheur_project/  
cd ..  
catkin clean -y && catkin build  
source devel/setup.bash  
```
#### Visualiser la urdf
```
source devel/setup.bash  
roslaunch part_one_urdf simulate.launch
```
#### Cinematique directe - un nœud permettant de contrôlerla jambe de manière directe
In the first terminal, execute the following:
```
cd catkin_ws/
catkin clean -y && catkin build  
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```
In the second terminal, execute the following:
```
cd catkin_ws/
source devel/setup.bash
roslaunch udm_project_control direct.launch
```
In the third terminal, execute the following: 
```
cd catkin_ws/
source devel/setup.bash
rosservice call /direct_kin_service_legmr "joint1:
 data: -0.3
joint2:
 data: -0.4
joint3:
 data: 0.1
joint4:
 data: -0.2"
 ```

##### Cinematique indirecte - un nœud permettant de contrôlerla jambe de manière indirecte
In the first terminal, execute the following:
```
cd catkin_ws/
catkin clean -y && catkin build  
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```
In the second terminal, execute the following:
```
cd catkin_ws/
source devel/setup.bash
roslaunch udm_project_control indirect.launch
```
In the third terminal, execute the following: 
```
cd catkin_ws/
source devel/setup.bash
rosservice call /indirect_kin_service_legmr "pose:
 orientation:
  w: 1
 position:
  x: 0.3
 position:
  y: 0.3
 position:
  z: -0.1"
 ```

## partie_2
### Partie 2 - Ajout des autres Jambes
The folder 'partie_2' corresponds to the second part of the project: "Ajout des autres Jambes". Additional information on the tp is available in the PDF file.  To run this section of the project, execute the following:

```
mkdir catkin_ws
cd catkin_ws
mkdir src
cd src
git clone https://github.com/azezezaaa/udm_ros_lerobotmarcheur_project  
mv udm_ros_lerobotmarcheur_project/partie_2/* . && rm -rf udm_ros_lerobotmarcheur_project/  
cd ..  
catkin clean -y && catkin build  
source devel/setup.bash  
```
#### Visualiser la urdf
```
source devel/setup.bash  
roslaunch part_two_urdf simulate.launch
```
#### Déplacer le robot en ligne droite, à gauche, à droite ou en arrière
In the first terminal, execute the following:
```
cd catkin_ws/
catkin clean -y && catkin build  
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```
In the second terminal, execute the following:
```
cd catkin_ws/
source devel/setup.bash
roslaunch udm_project_control control.launch
```
In the third terminal for 'front' displacement, execute the following: 
```
cd catkin_ws/
source devel/setup.bash
rosservice call /control "mouvement:
 data: 'front'" 
```
Change 'front' with 'right' , 'left' or 'back'.


## partie_3
### Partie 3 - Impact des Configurations
WIP
