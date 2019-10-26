FROM       fedora:30

# Install dnf overlay plugin to avoid rpmdb errors on overlayfs
RUN dnf install -y --nodocs dnf-plugin-ovl && dnf clean all

# Disable Delta RPM, since docs are stripped doesn't work
RUN echo "deltarpm=0" >> /etc/dnf/dnf.conf && \
	# Update and clean cache afterwards
	dnf -y --nodocs update && dnf clean all

# Enable COPR for libalvar, PDDL planners, plexil, and tensorflow
RUN dnf install -y --nodocs 'dnf-command(copr)' && \
	dnf -y copr enable thofmann/eclipse-clp-6 && \
	dnf -y copr enable thofmann/gologpp && \
	dnf -y copr enable thofmann/libalvar && \
	dnf -y copr enable thofmann/planner && \
	dnf -y copr enable thofmann/plexil && \
	dnf -y copr enable momosomium/tensorflow_c_api && \
	dnf clean all

# Install robotics related dependencies, be generous, skip docs
# Not in docker: ccache
# Exclude fedora-release:
# https://fedoraproject.org/wiki/Common_F30_bugs#Conflicts_between_fedora-release_packages_when_installing_package_groups
RUN dnf install -y --nodocs --excludepkg fedora-release \
  @buildsys-build @development-tools \
	gcc-c++ git make cmake hostname \
	doxygen doxygen-latex asciidoc docbook-style-xsl \
	kernel-headers elfutils-libelf-devel file-devel \
	yaml-cpp-devel PyYAML tinyxml-devel tinyxml2-devel libxslt xmlrpc-c-devel \
	libxml2-devel libxml++-devel python3-libxml2 apr-util-devel \
	boost-devel log4cxx-devel poco-devel readline-devel bzip2-devel \
	gperftools-devel gtest-devel libtool-ltdl-devel sqlite-devel \
	tbb-devel python-setuptools python2-numpy python2-pyopengl \
	avahi-devel bluez-libs-devel libmicrohttpd-devel libdaemon-devel \
  npm rapidjson-devel ctemplate-devel websocketpp-devel \
	openssl-devel libmodbus-devel \
	libjpeg-devel libpng-devel opencv-devel \
  orocos-kdl-devel orocos-bfl-devel \
	libalvar-devel libusb-devel hokuyoaist-devel libdc1394-devel libkni3-devel \
  librealsense1-devel libtensorflow_c-devel \
	libudev-devel urg-devel libkindrv-devel \
	flite-devel \
	urdfdom-headers-devel urdfdom-devel \
	bullet-devel CGAL-devel eigen3-devel \
	gts-devel libccd-devel pcl-devel player-devel openni-devel \
	protobuf-devel protobuf-compiler \
	graphviz graphviz-devel rrdtool-devel \
	mongo-cxx-driver-devel \
	assimp-devel freeimage-devel ogre-devel \
	mesa-libGL-devel mesa-libGLU-devel freeglut-devel \
	libXext-devel qt-devel PyQt4-devel fltk-devel \
	SDL-devel SDL_image-devel SDL_net-devel \
	cairomm gconfmm26-devel glibmm24-devel gtkmm30-devel \
	gazebo-devel gazebo-ode-devel gazebo-media \
	ros-release python-rospkg python3-rospkg console-bridge-devel \
	python-rosdistro python-rosinstall \
	python-rosinstall_generator python-wstool python3-rosdep python-rosdistro \
  python3-rosinstall_generator python3-rosinstall \
  python-qt5-devel python3-qt5-devel python2-defusedxml \
  sip-devel PyQt4-devel \
	python-netifaces \
	clips clipsmm-devel clips-emacs \
  plexil-devel plexil-compiler clingo-devel \
  eclipse-clp-devel gologpp-devel \
  fast-downward fast-forward \
	compat-lua compat-lua-devel compat-tolua++-devel \
	collada-dom-devel python-collada python-empy lz4-devel libuuid-devel \
	screen \
	&& dnf module install -y librealsense/dev \
	&& dnf clean all

