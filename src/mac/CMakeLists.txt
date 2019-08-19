# Mac options
option(ENABLE_MAC_BLAKE2 "Enable blake2" TRUE)
option(ENABLE_MAC_F9 "Enable f9" TRUE)
option(ENABLE_MAC_HMAC "Enable hmac" TRUE)
option(ENABLE_MAC_OMAC "Enable omac" TRUE)
option(ENABLE_MAC_PELICAN "Enable pelican" TRUE)
option(ENABLE_MAC_PMAC "Enable pmac" TRUE)
option(ENABLE_MAC_POLY1305 "Enable poly1305" TRUE)
option(ENABLE_MAC_XCBC "Enable xcbc" TRUE)

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
target_sources(${PROJECT_NAME}-shared PRIVATE ${MAC_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MAC_SOURCES})
