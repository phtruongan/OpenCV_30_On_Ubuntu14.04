# OpenCV_30_On_Ubuntu14.04
Description of the way install opencv 3.0 on ubuntu 14.04 and some programs on opencv
OPENCV and Ubutu 14.04
  - Install:
    - Step 1: Update and Upgrade ubuntu
      - $ sudo apt-get update
      - $ sudo apt-get upgrade
    - Step 2: Install our developer tools
      - $ sudo apt-get install build-essential cmake git pkg-config
    - Step 3: Softwares to load some image formats for opencv such as jpeg
      - $ sudo apt-get install libjpeg8-dev libtiff4-dev libjasper-dev libpng12-dev
    - Step 4: Install library for show the image to the screen after we can read the image on above step
      - $ sudo apt-get install libgtk2.0-dev
    - Step 5: Access individual frames
      - $ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
    - Step 6: Install libraries that optimize the routines of opencv
      - $ sudo apt-get install libatlas-base-dev gfortran
    - Step 7: Install pip, Python package manager
      - $ wget https://bootstrap.pypa.io/get-pip.py
      - $ sudo python get-pip.py
    - Step 8: Install virtual python and cv environment for each project we work on
      - $ sudo pip install virtualenv virtualenvwrapper
      - $ sudo rm -rf ~/.cache/pip
      - This step we must use everytime we want to work on python opencv projects:
        - $ export WORKON_HOME=$HOME/.virtualenvs
          $ source /usr/local/bin/virtualenvwrapper.sh
          $ source ~/bashrc
          $ mkvirtualenv cv
    - Step 9: Install python 2.7
      - $ sudo apt-get install python2.7-dev
      - $ pip install numpy         # this is useful for transforming image into array for easily processing
    - Step 10: Pull opencv 3.0.0 from github
      - $ cd ~
      - $ git clone https://github.com/Itseez/opencv.git
      - $ cd opencv
      - $ git checkout 3.0.0
      - Pull opencv_contrib from github
      - $ cd ~
      - $ git clone https://github.com/Itseez/opencv_contrib.git
      - $ cd opencv_contrib
      - $ git checkout 3.0.0
      - $ cd ~/opencv
      - $ mkdir build
      - $ cd build
      - $ cmake -D CMAKE_BUILD_TYPE=RELEASE \
	        -D CMAKE_INSTALL_PREFIX=/usr/local \
	        -D INSTALL_C_EXAMPLES=ON \
	        -D INSTALL_PYTHON_EXAMPLES=ON \
	        -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
	        -D BUILD_EXAMPLES=ON ..
      - $ make -j4    #take advantages of 4 cores to speedup
    - Install Opencv:
      - $sudo make install
      - $sudo ldconfig
    - Step 11: Go to cv environment
      - $ cd ~/.virtualenvs/cv/lib/python2.7/site-packages/
      - $ ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so
    - Step 12: run test opencv
      - $ workon cv
      - $ python
        >>> import cv2
        >>> cv2.__version__
        '3.0.0'
    - step 13: trial run example on opencv : python name.py
    
