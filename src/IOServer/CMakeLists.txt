
# SET(CMAKE_C_COMPILER g++)
# #SET (CMAKE_CXX_FLAGS_DEBUG "-g -Wall")
# #SET (CMAKE_BUILD_TYPE DEBUG)
# set(CMAKE_BUILD_TYPE "Debug")

# if( CMAKE_BUILD_TYPE STREQUAL "Debug" )
#     set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -Wall -Wno-unused-variable")
# else( CMAKE_BUILD_TYPE STREQUAL "Debug" )
#         set(CMAKE_BUILD_TYPE "Release")
#     set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2  -fopenmp")
# endif( CMAKE_BUILD_TYPE STREQUAL "Debug" )

message("Build Type: ${CMAKE_BUILD_TYPE} ${CMAKE_CXX_FLAGS}")

#FIND_PACKAGE(THREAD_DB REQUIRED)

#MARK_AS_ADVANCED(
#    THREAD_DB_INCLUDE_DIR
#    THREAD_DB_LIBRARY
#    )

# MESSAGE(STATUS ${THREAD_DB_INCLUDE_DIR} ${THREAD_DB_LIBRARY})

AUX_SOURCE_DIRECTORY(. DIR_SRCS)
MESSAGE(STATUS "main source file: ${DIR_SRCS}")
# SET(DIR_SRCS
#     main.cpp)
#保存位置
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin) 

LINK_DIRECTORIES(${PROJECT_BINARY_DIR}/lib)
LINK_DIRECTORIES(${PROJECT_BINARY_DIR}/bin)

ADD_EXECUTABLE(IOServer ${DIR_SRCS})

TARGET_LINK_LIBRARIES(IOServer 
                        RTDBCommon 
                        ACE 
                        RTDBDrvSheduleMgr 
                        RTDBNodeManager)

INSTALL(TARGETS IOServer RUNTIME DESTINATION bin)

