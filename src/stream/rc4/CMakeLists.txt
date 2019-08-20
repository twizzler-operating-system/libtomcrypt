set(STREAM_RC4_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/rc4_stream.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc4_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc4_stream_memory.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${STREAM_RC4_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${STREAM_RC4_SOURCES})
