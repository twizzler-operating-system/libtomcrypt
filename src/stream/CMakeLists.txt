# Stream options
option(ENABLE_STREAM_CHACHA "Enable chacha stream" TRUE)
option(ENABLE_STREAM_RABBIT "Enable rabbit stream" TRUE)
option(ENABLE_STREAM_RC4 "Enable rc4 stream" TRUE)
option(ENABLE_STREAM_SALSA20 "Enable salsa20 stream" TRUE)
option(ENABLE_STREAM_SOBER128 "Enable sober128 stream" TRUE)
option(ENABLE_STREAM_SOSEMANUK "Enable sosemanuk stream" TRUE)

set(STREAM_SOURCES)

if(ENABLE_STREAM_CHACHA)
    add_subdirectory(chacha)
    list(APPEND STREAM_SOURCES ${STREAM_CHACHA_SOURCES})
endif()

if(ENABLE_STREAM_RABBIT)
    add_subdirectory(rabbit)
    list(APPEND STREAM_SOURCES ${STREAM_RABBIT_SOURCES})
endif()

if(ENABLE_STREAM_RC4)
    add_subdirectory(rc4)
    list(APPEND STREAM_SOURCES ${STREAM_RC4_SOURCES})
endif()

if(ENABLE_STREAM_SALSA20)
    add_subdirectory(salsa20)
    list(APPEND STREAM_SOURCES ${STREAM_SALSA20_SOURCES})
endif()

if(ENABLE_STREAM_SOBER128)
    add_subdirectory(sober128)
    list(APPEND STREAM_SOURCES ${STREAM_SOBER128_SOURCES})
endif()

if(ENABLE_STREAM_SOSEMANUK)
    add_subdirectory(sosemanuk)
    list(APPEND STREAM_SOURCES ${STREAM_SOSEMANUK_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Stream
#-----------------------------------------------------------------------------
add_library(stream_shared_obj OBJECT
    ${STREAM_SOURCES}
)

add_library(stream_static_obj OBJECT
    ${STREAM_SOURCES}
)

set_target_properties(stream_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
