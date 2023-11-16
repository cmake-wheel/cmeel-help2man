cmake_minimum_required(VERSION 3.20)

set(HELP2MAN_VERSION 1.49.3)

project(cmeel-help2man VERSION ${HELP2MAN_VERSION})

include(ExternalProject)
ExternalProject_Add(
  help2man
  URL "https://ftpmirror.gnu.org/gnu/help2man/help2man-${HELP2MAN_VERSION}.tar.xz"
  URL_HASH "SHA1=3ed88430c97af3c5b57949f6f030b913044af507"
  DOWNLOAD_EXTRACT_TIMESTAMP OFF
  BUILD_IN_SOURCE ON
  CONFIGURE_COMMAND "./configure" "--prefix=${CMAKE_INSTALL_PREFIX}"
  # "--with-bugurl=https://github.com/cmake-wheel/cmeel-help2man/issues"
  BUILD_COMMAND "make"
  INSTALL_COMMAND "make" "install")

# dummy file for install target
install(FILES README.md DESTINATION share/cmeel-help2man/)
