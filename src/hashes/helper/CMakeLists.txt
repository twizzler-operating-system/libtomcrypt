set(HASH_HELPER_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/hash_filehandle.c
    ${CMAKE_CURRENT_SOURCE_DIR}/hash_file.c
    ${CMAKE_CURRENT_SOURCE_DIR}/hash_memory_multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/hash_memory.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${HASH_HELPER_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${HASH_HELPER_SOURCES})
