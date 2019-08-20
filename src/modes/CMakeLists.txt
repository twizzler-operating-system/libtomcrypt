#-----------------------------------------------------------------------------
# Modes options
#-----------------------------------------------------------------------------
option(ENABLE_MODE_CBC "Enable cbc mode" TRUE)
option(ENABLE_MODE_CFB "Enable cfb mode" TRUE)
option(ENABLE_MODE_CTR "Enable ctr mode" TRUE)
option(ENABLE_MODE_ECB "Enable ecb mode" TRUE)
option(ENABLE_MODE_F8 "Enable f8 mode" TRUE)
option(ENABLE_MODE_LRW "Enable lrw mode" TRUE)
option(ENABLE_MODE_OFB "Enable ofb mode" TRUE)
option(ENABLE_MODE_XTS "Enable xts mode" TRUE)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------

if(ENABLE_MODE_CBC)
    add_subdirectory(cbc)
endif()

if(ENABLE_MODE_CFB)
    add_subdirectory(cfb)
endif()

if(ENABLE_MODE_CTR)
    add_subdirectory(ctr)
endif()

if(ENABLE_MODE_ECB)
    add_subdirectory(ecb)
endif()

if(ENABLE_MODE_F8)
    add_subdirectory(f8)
endif()

if(ENABLE_MODE_LRW)
    add_subdirectory(lrw)
endif()

if(ENABLE_MODE_OFB)
    add_subdirectory(ofb)
endif()

if(ENABLE_MODE_XTS)
    add_subdirectory(xts)
endif()
