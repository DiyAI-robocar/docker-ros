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
RUN echo >>/root/.ssh/authorized_keys ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5Ag6aNP8oC8A50Q18z/ZIvTG+rZqaDdQEg7olhPh2+3vPJFuBvKSSY6BodVMffR3DwCpfN/WCMclxHMssavE4ZCh83U35WtFyuXBIs8X54vIHPEj08+wSU83Zee/U229JnyVtjCJa2VKQgkxA2vxs8I+fKFpijjD0mgihgAG+N7/F1lSO0jaAQBQJVCOpg6FVqTUcSdGu6CIBTpqXTenBrOjEYfgdHcMBmAWBm/jtrjyep9vC3WLYxsG0XHzBKD8/H5s6HoX6SSbKxCSM/uIO1fmbWZVqnHxPnKLWuLigZrESaVOKo+1ABiebcxprH4mgdMeCr58rwcIBlhdW2YSJ af1n@af1n-toshiba
RUN chmod 600 /root/.ssh/authorized_keys
RUN mkdir /run/sshd
CMD /usr/sbin/sshd -D -p 2222
