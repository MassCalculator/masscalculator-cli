cmake_minimum_required(VERSION 3.15)

################################################################################
#
# Project definition
#
################################################################################

# Define the project
project(masscalculator-cli
        VERSION 0.1.0
        HOMEPAGE_URL "https://github.com/MassCalculator/masscalculator-cli"
        DESCRIPTION "masscalculator-cli executable"
        LANGUAGES CXX
)

# Set C and C++ standards
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Set the project version.
set(MASSCALCULATOR_CLI_NAME ${PROJECT_NAME})
set(MASSCALCULATOR_CLI_VERSION ${PROJECT_VERSION})
set(MASSCALCULATOR_CLI_MAJOR ${PROJECT_VERSION_MAJOR})
set(MASSCALCULATOR_CLI_MINOR ${PROJECT_VERSION_MINOR})
set(MASSCALCULATOR_CLI_PATCH ${PROJECT_VERSION_PATCH})

################################################################################
#
# Additional CMake functionalities
#
################################################################################

# Additional CMake modules are added here to allow finding libraries not
# natively supported by CMake and to be able to include CMake files
# uder third_party/ redirectly.
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH}
  "${CMAKE_SOURCE_DIR}/cmake"
)

# Initialize the package manager.
include(conan)

################################################################################
#
# CMake targets definition
#
################################################################################

if(${BUILD_DOCS})
  # This adds the doxygen documentation.
  add_subdirectory(docs)
endif()

# This adds the masscalculator command line interface.
add_subdirectory(masscalculator-cli)

# This adds the compile flags.
target_compile_options(${PROJECT_NAME} PRIVATE -O2 -Wall -Wextra -Werror)

# This adds the linker flags.
target_link_options(${PROJECT_NAME} PRIVATE -flto)

################################################################################
#
# Installation and Deployment
#
################################################################################

include(install)

# This adds the packaging steps.
# @todo(jimmyhalimi): Commented out for now, until time comes to fix this.
# include(pack-cpack)

if(${BUILD_RELEASE})
  # @todo(jimmyhalimi): Commented out for now, until time comes to fix this.
  # include(deploy)
endif()
