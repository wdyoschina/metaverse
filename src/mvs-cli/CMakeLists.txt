
FILE(GLOB_RECURSE mvs-cli_SOURCES "*.cpp")

ADD_DEFINITIONS(-DBCX_STATIC=1)

ADD_EXECUTABLE(mvs-cli ${mvs-cli_SOURCES})

# for experimental/string_view
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-deprecated-declarations")

IF(ENABLE_SHARED_LIBS)
    TARGET_LINK_LIBRARIES(mvs-cli ${mongoose_LIBRARY} ${jsoncpp_LIBRARY}
        ${bitcoin_LIBRARY} ${explorer_LIBRARY})
ELSE()
    TARGET_LINK_LIBRARIES(mvs-cli ${mongoose_LIBRARY} ${jsoncpp_LIBRARY}
        ${bitcoin_LIBRARY} ${explorer_LIBRARY})
ENDIF()

INSTALL(TARGETS mvs-cli DESTINATION bin)
