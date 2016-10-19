# Script generated with Bloom
pkgdesc="ROS - Package modeling the run-time dependencies for language bindings of messages."
url='http://ros.org/wiki/message_runtime'

pkgname='ros-minimalist-message-runtime'
pkgver='0.4.12'
pkgrel='0'
arch=('any')
license=('BSD')

makedepends=('ros-minimalist-catkin'
)

depends=('ros-minimalist-cpp-common'
'ros-minimalist-genpy'
'ros-minimalist-roscpp-serialization'
'ros-minimalist-roscpp-traits'
'ros-minimalist-rostime'
)

conflicts=()
replaces=()

_dir=message_runtime
source=()
md5sums=()

prepare() {
    cp -R $startdir/message_runtime $srcdir/message_runtime
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/minimalist/setup.bash ] && source /opt/ros/minimalist/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/minimalist \
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

