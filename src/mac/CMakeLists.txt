set(MAC_SOURCES)

if(ENABLE_MAC_BLAKE2)
    add_subdirectory(blake2)
    list(APPEND MAC_SOURCES ${MAC_BLAKE2_SOURCES})
endif()

if(ENABLE_MAC_F9)
    add_subdirectory(f9)
    list(APPEND MAC_SOURCES ${MAC_F9_SOURCES})
endif()

if(ENABLE_MAC_HMAC)
    add_subdirectory(hmac)
    list(APPEND MAC_SOURCES ${MAC_HMAC_SOURCES})
endif()

if(ENABLE_MAC_OMAC)
    add_subdirectory(omac)
    list(APPEND MAC_SOURCES ${MAC_OMAC_SOURCES})
endif()

if(ENABLE_MAC_PELICAN)
    add_subdirectory(pelican)
    list(APPEND MAC_SOURCES ${MAC_PELICAN_SOURCES})
endif()

if(ENABLE_MAC_PMAC)
    add_subdirectory(pmac)
    list(APPEND MAC_SOURCES ${MAC_PMAC_SOURCES})
endif()

if(ENABLE_MAC_POLY1305)
    add_subdirectory(poly1305)
    list(APPEND MAC_SOURCES ${MAC_POLY1305_SOURCES})
endif()

if(ENABLE_MAC_XCBC)
    add_subdirectory(xcbc)
    list(APPEND MAC_SOURCES ${MAC_XCBC_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Mac
#-----------------------------------------------------------------------------
add_library(mac_shared_obj OBJECT
    ${MAC_SOURCES}
)

add_library(mac_static_obj OBJECT
    ${MAC_SOURCES}
)

set_target_properties(mac_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
