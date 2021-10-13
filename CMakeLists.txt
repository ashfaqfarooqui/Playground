cmake_minimum_required(VERSION 3.11.3)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(Playground)

# Enable strict handling of warnings
add_definitions("-Wall -Wextra -Werror")

# Finds MAVSDK when installed system wide.
# Maybe in the future build it locally.
find_package(MAVSDK REQUIRED)


# Specify your app's executable name, and list of source files used to create it.
add_executable(droneControl
    src/main.cpp
    # ... any other source files
)

target_link_libraries(droneControl
    MAVSDK::mavsdk             #All apps link against mavsdk library
    MAVSDK::mavsdk_action      # If action plugin used by app ...
    MAVSDK::mavsdk_telemetry   #If telemetry plugin used by app ...
    )
