include("${CODAL_UTILS_LOCATION}")
RECURSIVE_FIND_DIR(INCLUDE_DIRS "./inc" "*.h")
RECURSIVE_FIND_FILE(SOURCE_FILES "./source" "*.c??")

#execute_process(WORKING_DIRECTORY "." COMMAND "git" "log" "--pretty=format:%h" "-n" "1" OUTPUT_VARIABLE git_hash)
#execute_process(WORKING_DIRECTORY "." COMMAND "git" "rev-parse" "--abbrev-ref" "HEAD" OUTPUT_VARIABLE git_branch OUTPUT_STRIP_TRAILING_WHITESPACE)

#if ("${git_branch}" STREQUAL "master")
#    set(CODAL_VERSION_STRING "${CODAL_VERSION_STRING}")
#else()
#    set(CODAL_VERSION_STRING "${CODAL_VERSION_STRING}-${git_branch}-g${git_hash}")
#endif()

#set(CODAL_VERSION_FLAGS "-DCODAL_VERSION=\\\"${CODAL_VERSION_STRING}\\\"")

#set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${CODAL_VERSION_FLAGS}")

# add them
include_directories(${INCLUDE_DIRS})

add_library(codal-microbit-v2-arduino-compat
    ${SOURCE_FILES}
)

#target_link_libraries()

target_include_directories(codal-microbit-v2-arduino-compat PUBLIC ${INCLUDE_DIRS})