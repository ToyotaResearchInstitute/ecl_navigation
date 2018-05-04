##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_mobile_robot)

##############################################################################
# Find Packages
##############################################################################

find_package(ament_cmake_ros REQUIRED)
find_package(ecl_build REQUIRED)
find_package(ecl_errors REQUIRED)
find_package(ecl_geometry REQUIRED)
find_package(ecl_math REQUIRED)
find_package(ecl_formatters REQUIRED)
find_package(ecl_linear_algebra REQUIRED)

##############################################################################
# Project Configuration
##############################################################################

ecl_enable_cxx14_compiler()

##############################################################################
# Sources
##############################################################################

add_subdirectory(include)
add_subdirectory(src)

##############################################################################
# Exports
##############################################################################

ament_export_interfaces(${PROJECT_NAME})
ament_export_dependencies(
    ecl_errors
    ecl_geometry
    ecl_math
    ecl_formatters
    ecl_linear_algebra
)
ament_package()
