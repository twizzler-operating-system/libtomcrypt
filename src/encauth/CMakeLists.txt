# Encauth options
option(ENABLE_ENCAUTH_CCM "Enable ccm" TRUE)
option(ENABLE_ENCAUTH_CHACHAPOLY "Enable chachapoly" TRUE)
option(ENABLE_ENCAUTH_EAX "Enable eax" TRUE)
option(ENABLE_ENCAUTH_GCM "Enable gcm" TRUE)
option(ENABLE_ENCAUTH_OCB "Enable ocb" TRUE)
option(ENABLE_ENCAUTH_OCB3 "Enable ocb3" TRUE)

set(ENCAUTH_SOURCES)

if(ENABLE_ENCAUTH_CCM)
    add_subdirectory(ccm)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_CCM_SOURCES})
endif()

if(ENABLE_ENCAUTH_CHACHAPOLY)
    add_subdirectory(chachapoly)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_CHACHAPOLY_SOURCES})
endif()

if(ENABLE_ENCAUTH_EAX)
    add_subdirectory(eax)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_EAX_SOURCES})
endif()

if(ENABLE_ENCAUTH_GCM)
    add_subdirectory(gcm)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_GCM_SOURCES})
endif()

if(ENABLE_ENCAUTH_OCB)
    add_subdirectory(ocb)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_OCB_SOURCES})
endif()

if(ENABLE_ENCAUTH_OCB3)
    add_subdirectory(ocb3)
    list(APPEND ENCAUTH_SOURCES ${ENCAUTH_OCB3_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Encauth
#-----------------------------------------------------------------------------

target_sources(${PROJECT_NAME}-shared PRIVATE ${ENCAUTH_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${ENCAUTH_SOURCES})
