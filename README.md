# drone_iris_simulation
Archivos necesarios para ejecutar la simulación del dron iris

Para realizar una correcta simulación del dron iris, se debe clonar este repositorio y también se debe clonar el repositorio que se encuentra en la página oficial de ardupilot (ardupilot.org). Además de esto se deben instalar algunos programas tales como: Gazebo9, ROS (se recomienda melodic), QGroundControl, MAVProxy, MAVlink y contar con python.

También cabe mencionar que esta simulación ha sido probada en ubuntu 18.04 por lo cual se recomienda utilizar esta version

A continuación se muestra a manera de tutorial, los comandos para clonar los repositorios y para instalar los complementos necesarios.


# Clonar este repositorio:

git clone https://github.com/Sebastian2218/drone_iris_simulation.git  

cd drone_iris_simulation

cd ardupilot_gazebo

mkdir build

cd build

cmake ..

make -j4

sudo make install


# Clonar el repositorio de ardupilot: (Se recomienda clonar el repositorio dentro de la carpeta generada al clonar el repositorio anterior)

cd drone_iris_simulation                                                  

git clone https://github.com/ArduPilot/ardupilot.git  

cd ardupilot

git submodule update --init --recursive


# Instalar Gazebo 9:

Nota: Las siguientes dos líneas corresponden a un mismo comando

sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'  

wget https://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add - s

sudo apt-get update    

sudo apt-get install gazebo9  

sudo apt-get install libgazebo9-dev     


# Instalar ROS melodic:

sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' 

Nota: Las siguientes dos líneas corresponden a un mismo comando

sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

sudo apt update

sudo apt install ros-melodic-desktop-full

apt search ros-melodic

echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

source ~/.bashrc

sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

sudo apt install python-rosdep

sudo rosdep init

rosdep update


# Instalar pip:

sudo apt update                   

sudo apt install python-pip       


# Instalar python:

sudo apt-get install python           


# Instalar MAVProxy:

sudo pip install MAVProxy            


# Instalar MAVLink:

sudo pip install pymavlink            


# Instalar QGroundControl:

sudo usermod -a -G dialout $USER

sudo apt-get remove modemmanager

wget https://s3-us-west-2.amazonaws.com/qgroundcontrol/latest/QGroundControl.AppImage

chmod +x ./QGroundControl.AppImage


Una vez se han clonado exitosamente los repositorios e instalado correctamente los complementos se procede a correr la simulación, para esto se deben ejecutar los comandos que se encuentran en el archivo comandos_dron_iris.txt que se encuentra en este repositorio.


Para una mejor visualización en gazebo, en la parte superior izquerda nos dirigimos a la ventana World>Models>iris_demo y damos click derecho sobre iris_demo, posteriormente damos click en "Follow"


Cuando se lanza la simulación desde QGroundControl, primero se deben armar los motores, luego se le da al boton de "takeoff" y se selecciona la altura deseada. Para manipular el dron con el joystick se debe seleccionar el modo de vuelo "ZigZag"
