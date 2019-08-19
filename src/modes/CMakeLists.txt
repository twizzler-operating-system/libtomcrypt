# Modes options
option(ENABLE_MODE_CBC "Enable cbc mode" TRUE)
option(ENABLE_MODE_CFB "Enable cfb mode" TRUE)
option(ENABLE_MODE_CTR "Enable ctr mode" TRUE)
option(ENABLE_MODE_ECB "Enable ecb mode" TRUE)
option(ENABLE_MODE_F8 "Enable f8 mode" TRUE)
option(ENABLE_MODE_LRW "Enable lrw mode" TRUE)
option(ENABLE_MODE_OFB "Enable ofb mode" TRUE)
option(ENABLE_MODE_XTS "Enable xts mode" TRUE)

set(MODES_SOURCES)

if(ENABLE_MODE_CBC)
    add_subdirectory(cbc)
    list(APPEND MODES_SOURCES ${MODE_CBC_SOURCES})
endif()

if(ENABLE_MODE_CFB)
    add_subdirectory(cfb)
    list(APPEND MODES_SOURCES ${MODE_CFB_SOURCES})
endif()

if(ENABLE_MODE_CTR)
    add_subdirectory(ctr)
    list(APPEND MODES_SOURCES ${MODE_CTR_SOURCES})
endif()

if(ENABLE_MODE_ECB)
    add_subdirectory(ecb)
    list(APPEND MODES_SOURCES ${MODE_ECB_SOURCES})
endif()

if(ENABLE_MODE_F8)
    add_subdirectory(f8)
    list(APPEND MODES_SOURCES ${MODE_F8_SOURCES})
endif()

if(ENABLE_MODE_LRW)
    add_subdirectory(lrw)
    list(APPEND MODES_SOURCES ${MODE_LRW_SOURCES})
endif()

if(ENABLE_MODE_OFB)
    add_subdirectory(ofb)
    list(APPEND MODES_SOURCES ${MODE_OFB_SOURCES})
endif()

if(ENABLE_MODE_XTS)
    add_subdirectory(xts)
    list(APPEND MODES_SOURCES ${MODE_XTS_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Modes
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${MODES_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODES_SOURCES})
