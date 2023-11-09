FROM ubuntu

RUN apt update && apt upgrade -y
RUN apt autoremove

RUN apt install python3-colcon-common-extensions
RUN echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc

WORKDIR /root/${ros2_ws}
RUN mkdir src
RUN colcon build

RUN echo "source root/{ros2_ws}/install/setup.bash" >> ~/.bashrc

RUN apt install python3-pip
RUN pip3 install setuptools==58.2.0

WORKDIR /root/${ros2_ws}/src
RUN ros2 pkg create my_py_pkg --build-type ament_python --dependencies rclpy

WORKDIR /root/${ros2_ws}/src
RUN colcon build
