FROM ros:melodic-robot
# install ros tutorials packages
RUN apt-get update && apt-get install -y \
    ros-melodic-ros-tutorials \
    ros-melodic-common-tutorials \
    tmux screen vim wget curl iputils-ping mtr tcpdump openssh-server mc
#RUN TERM=linux wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it && ~/.bash_it/install.sh
RUN sed s/bobby/candy/g -i /root/.bashrc
RUN echo >>/root/.bashrc export ROS_DISTRO=melodic
RUN echo >>/root/.bashrc export ROS_HOSTNAME=playground
RUN echo >>/root/.bashrc export ROS_MASTER_URI=http://master:11311
RUN echo >>/root/.bashrc source /ros_entrypoint.sh
RUN echo >>/root/.bashrc set +e
RUN mkdir /root/.ssh
RUN mkdir /run/sshd
RUN sed -i 's/#X11UseLocalhost yes/X11UseLocalhost no/' /etc/ssh/sshd_config
ADD authorized_keys /root/.ssh/authorized_keys
RUN chmod 600 /root/.ssh/authorized_keys
CMD /usr/sbin/sshd -D -p 2222
