add_subdirectory(linuxdeploy EXCLUDE_FROM_ALL)
if(NOT TARGET gtest AND BUILD_TESTING)
    add_subdirectory(googletest EXCLUDE_FROM_ALL)
endif()

# required to properly build nlohmann/json v. 2.0.0 on trusty
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(json INTERFACE)
set_property(TARGET json PROPERTY INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/json/include)
target_sources(json INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/json/include/json.hpp)
