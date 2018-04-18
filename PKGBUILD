# Script generated with Bloom
pkgdesc="ROS - Python and C++ interfaces for manipulating geodetic coordinates."
url='http://wiki.ros.org/geodesy'

pkgname='ros-melodic-geodesy'
pkgver='0.5.3_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python2-catkin_pkg'
'ros-melodic-angles'
'ros-melodic-catkin'
'ros-melodic-geographic-msgs'
'ros-melodic-geometry-msgs'
'ros-melodic-rosunit'
'ros-melodic-sensor-msgs'
'ros-melodic-tf'
'ros-melodic-unique-id'
'ros-melodic-uuid-msgs'
)

depends=('python2-pyproj'
'ros-melodic-geographic-msgs'
'ros-melodic-geometry-msgs'
'ros-melodic-sensor-msgs'
'ros-melodic-tf'
'ros-melodic-unique-id'
'ros-melodic-uuid-msgs'
)

conflicts=()
replaces=()

_dir=geodesy
source=()
md5sums=()

prepare() {
    cp -R $startdir/geodesy $srcdir/geodesy
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

