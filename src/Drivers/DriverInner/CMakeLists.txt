ADD_DEFINITIONS(-DDRIVERINNER_EXPORTS)

AUX_SOURCE_DIRECTORY(. DIR_FEPIOINNERDRV_SRCS)

MESSAGE(STATUS "FepIOInnerDrv source file: ${DIR_FEPIOINNERDRV_SRCS}")

#保存位置
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin/Driver)

LINK_DIRECTORIES(${PROJECT_BINARY_DIR}/lib)
LINK_DIRECTORIES(${PROJECT_BINARY_DIR}/bin)

ADD_LIBRARY(FepIOInnerDrv SHARED ${DIR_FEPIOINNERDRV_SRCS})

TARGET_LINK_LIBRARIES(FepIOInnerDrv ACE RTDBCommon RTDBBaseClasses RTDBDriverFrame)

