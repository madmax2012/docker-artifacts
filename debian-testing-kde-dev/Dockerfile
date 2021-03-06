# Copyright (c) 2018 Jakob Meng, <jakobmeng@web.de>
# 
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.

FROM jm1337/debian-testing-dev

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
  apt-get install -y \
    libboost-all-dev libc++-dev libcrypto++-dev libopencv-dev libgoogle-perftools-dev liblapack-dev liblapacke-dev libopencv-dev libmbedtls-dev libusb-1.0-0-dev libxml2-dev libclang-dev \
    qml qt5-qmake qtcreator "libqt5.*-dev" "libqt5*-dev" "qt*5-dev" "qt*5-private-dev" "qt*5-dev-tools" \
    libkchart-dev libdwarf-dev libsparsehash-dev libzstd-dev \
    \
    libbz2-dev libxslt-dev libxml2-dev libgif-dev libvlc-dev libvlccore-dev libxapian-dev fontforge libgcrypt20-dev \
    libattr1-dev network-manager-dev libgtk-3-dev xsltproc xserver-xorg-dev xserver-xorg-input-synaptics-dev \
    libpwquality-dev modemmanager-dev libxcb-keysyms1-dev libepoxy-dev libpolkit-agent-1-dev libegl1-mesa-dev \
    libxcb-xkb-dev libwww-perl libxml-parser-perl libjson-perl libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev \
    libarchive-dev liblmdb-dev libsvn-dev libnm-dev \
    \
    okteta okteta-dev breeze-icon-theme konsole-kpart ninja-build \
    breeze oxygen-icon-theme plasma-integration konsole kate dolphin systemsettings \
    kde-sc-dev-latest \
    libomp-dev libnetcdf-c++4-dev libnetcdf-dev netcdf-bin libvtk6-dev python-vtk6 paraview \
    'libkf5([^k]+|(k([^f]|$)|kf([^a]|$)|kfa([^c]|$)|kfac([^e]|$)))+.*dev' \
    plasma-framework plasma-workspace-dev kdoctools-dev \
    plasma-workspace-wayland \
    python-docutils \
    kde-l10n-de \
    libgrantlee5-dev libkomparediff2-dev heaptrack heaptrack-gui \
    bison flex \
    mesa-utils \
    && \
  apt-get clean

# NOTE:
# - libomp-dev is OpenMP; it is required e.g. to build code generated by MATLAB Coder
# - libnetcdf-c++4-dev and libnetcdf-dev are for handling netCDF files as used for Grids in DLRs TAU
# - libvtk6-dev and paraview are for reading/writing and visualizing *.vtk files as produced by tau2vtk
# - in Debian Stretch and later libpolarssl-dev has been renamed to libmbedtls-dev
# - list of packages that will be build by kdesrc-build: libkomparediff2-dev libgrantlee-dev
# - python-docutils is for rst2html command used by kdevelop for (better) documentation display
# - Debian Stretch packages libcv-dev, libcvaux-dev and libhighgui-dev have been replaced by libopencv-dev in Debian Sid
# - transitional package plasma-framework-dev (depends on libkf5plasma-dev) has been removed from sid
# - libkf5kface-dev depends on libkf5kface10.0.0 which in sid is build against old opencv packages that 
#   have already been removed from repository. Thus instead of depending on "libkf5.*-dev" we ignore
#   libkf5kface-dev by use of a posix regular expression.
# - libnm-glib-dev, libnm-glib-vpn-dev and libnm-util-dev are deprecated since network-manager 1.12.0-4

ENV XDG_CURRENT_DESKTOP=KDE

ADD prepare-container.d/* /etc/prepare-container.d/
ADD prepare-container.service.d/* /etc/systemd/system/prepare-container.service.d/
