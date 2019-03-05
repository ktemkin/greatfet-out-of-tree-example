#
# Example of building an out-of-tree firmware against GreatFET.
#

cmake_minimum_required(VERSION 3.1.3)

# Check to make sure the user has specified the path to the GreatFET build tree.
if(NOT DEFINED ENV{GREATFET_PATH})
  message(FATAL_ERROR "GREATFET_PATH must be defined to point to your GreatFET tree.")
endif()

# Declare our project, and pull in the necessary GreatFET functionality.
include($ENV{GREATFET_PATH}/firmware/cmake/greatfet_prelude.cmake)
project(blinky_external C ASM)
include(${PATH_GREATFET_FIRMWARE_CMAKE}/greatfet.cmake)

# Add the code for our target. Using `add_greatfet_targets` ensures we'll get our standard flash/programming targets.
add_greatfet_targets(${PROJECT_NAME}
	blinky.c
)

# Use drivers from libgreat -- here, we'll pull in only the libgreat GPIO driver.
use_libgreat_modules(${PROJECT_NAME} gpio)
