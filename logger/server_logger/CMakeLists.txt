add_subdirectory(tests)

include(FetchContent)

FetchContent_Declare(httplib SYSTEM
        GIT_REPOSITORY https://github.com/yhirose/cpp-httplib
        GIT_TAG a609330e4c6374f741d3b369269f7848255e1954 # v0.14.1
        GIT_SHALLOW TRUE)
FetchContent_MakeAvailable(httplib)

add_library(
        mp_os_lggr_srvr_lggr
        src/server_logger.cpp
        src/server_logger_builder.cpp)

include_directories(${VCPKG_INCLUDE_DIRS})

target_include_directories(
        mp_os_lggr_srvr_lggr
        PUBLIC
        ./include
        ${VCPKG_INCLUDE_DIRS}
)

target_link_libraries(
        mp_os_lggr_srvr_lggr
        PUBLIC
        mp_os_cmmn)
target_link_libraries(
        mp_os_lggr_srvr_lggr
        PUBLIC
        mp_os_lggr_lggr)
target_link_libraries(
        mp_os_lggr_srvr_lggr
        PUBLIC
        nlohmann_json::nlohmann_json)
target_link_libraries(mp_os_lggr_srvr_lggr PRIVATE ws2_32)