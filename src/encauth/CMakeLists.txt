#-----------------------------------------------------------------------------
# Encauth options
#-----------------------------------------------------------------------------
option(ENABLE_ENCAUTH_CCM "Enable ccm" TRUE)
option(ENABLE_ENCAUTH_CHACHAPOLY "Enable chachapoly" TRUE)
option(ENABLE_ENCAUTH_EAX "Enable eax" TRUE)
option(ENABLE_ENCAUTH_GCM "Enable gcm" TRUE)
option(ENABLE_ENCAUTH_OCB "Enable ocb" TRUE)
option(ENABLE_ENCAUTH_OCB3 "Enable ocb3" TRUE)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
if(ENABLE_ENCAUTH_CCM)
    add_subdirectory(ccm)
endif()

if(ENABLE_ENCAUTH_CHACHAPOLY)
    add_subdirectory(chachapoly)
endif()

if(ENABLE_ENCAUTH_EAX)
    add_subdirectory(eax)
endif()

if(ENABLE_ENCAUTH_GCM)
    add_subdirectory(gcm)
endif()

if(ENABLE_ENCAUTH_OCB)
    add_subdirectory(ocb)
endif()

if(ENABLE_ENCAUTH_OCB3)
    add_subdirectory(ocb3)
endif()
