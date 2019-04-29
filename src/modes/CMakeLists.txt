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
add_library(modes_shared_obj OBJECT
    ${MODES_SOURCES}
)

add_library(modes_static_obj OBJECT
    ${MODES_SOURCES}
)

set_target_properties(modes_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
