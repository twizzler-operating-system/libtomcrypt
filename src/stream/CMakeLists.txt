#-----------------------------------------------------------------------------
# Stream options
#-----------------------------------------------------------------------------
option(ENABLE_STREAM_CHACHA "Enable chacha stream" TRUE)
option(ENABLE_STREAM_RABBIT "Enable rabbit stream" TRUE)
option(ENABLE_STREAM_RC4 "Enable rc4 stream" TRUE)
option(ENABLE_STREAM_SALSA20 "Enable salsa20 stream" TRUE)
option(ENABLE_STREAM_SOBER128 "Enable sober128 stream" TRUE)
option(ENABLE_STREAM_SOSEMANUK "Enable sosemanuk stream" TRUE)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
if(ENABLE_STREAM_CHACHA)
    add_subdirectory(chacha)
endif()

if(ENABLE_STREAM_RABBIT)
    add_subdirectory(rabbit)
endif()

if(ENABLE_STREAM_RC4)
    add_subdirectory(rc4)
endif()

if(ENABLE_STREAM_SALSA20)
    add_subdirectory(salsa20)
endif()

if(ENABLE_STREAM_SOBER128)
    add_subdirectory(sober128)
endif()

if(ENABLE_STREAM_SOSEMANUK)
    add_subdirectory(sosemanuk)
endif()
