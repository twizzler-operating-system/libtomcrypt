#-----------------------------------------------------------------------------
# Mac options
#-----------------------------------------------------------------------------
option(ENABLE_MAC_BLAKE2 "Enable blake2" TRUE)
option(ENABLE_MAC_F9 "Enable f9" TRUE)
option(ENABLE_MAC_HMAC "Enable hmac" TRUE)
option(ENABLE_MAC_OMAC "Enable omac" TRUE)
option(ENABLE_MAC_PELICAN "Enable pelican" TRUE)
option(ENABLE_MAC_PMAC "Enable pmac" TRUE)
option(ENABLE_MAC_POLY1305 "Enable poly1305" TRUE)
option(ENABLE_MAC_XCBC "Enable xcbc" TRUE)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
if(ENABLE_MAC_BLAKE2)
    add_subdirectory(blake2)
endif()

if(ENABLE_MAC_F9)
    add_subdirectory(f9)
endif()

if(ENABLE_MAC_HMAC)
    add_subdirectory(hmac)
endif()

if(ENABLE_MAC_OMAC)
    add_subdirectory(omac)
endif()

if(ENABLE_MAC_PELICAN)
    add_subdirectory(pelican)
endif()

if(ENABLE_MAC_PMAC)
    add_subdirectory(pmac)
endif()

if(ENABLE_MAC_POLY1305)
    add_subdirectory(poly1305)
endif()

if(ENABLE_MAC_XCBC)
    add_subdirectory(xcbc)
endif()
