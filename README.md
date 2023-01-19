Install ardupilot-

    git clone https://github.com/ArduPilot/ardupilot.git
      
Install dependencies-

    cd ardupilot
    Tools/environment_install/install-prereqs-ubuntu.sh -y
     
Reload profile-

     . ~/.profile
     
Latest copter build-  

     git checkout Copter-4.3.2
     git submodule update --init --recursive
   
Install ardupilot gazebo plugin-

     git clone https://github.com/khancyr/ardupilot_gazebo.git
      
Build and install plugin (@ardupilot_gazebo)-

     mkdir build
     cd build
     cmake ..
     make -j4
     sudo make install
      
 Source the files-
 
     echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
      
 Set model path-
 
     echo 'export GAZEBO_MODEL_PATH=~/ardupilot_gazebo/models' >> ~/.bashrc
     . ~/.bashrc

To run the simulation, in one terminal-

     gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world
      
 another terminal (this is the SITL)-
 
      cd ~/ardupilot/ArduCopter/
      sim_vehicle.py -v ArduCopter -f gazebo-iris --console
