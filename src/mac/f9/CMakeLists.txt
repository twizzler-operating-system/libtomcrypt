set(MAC_F9_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_file.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_process.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f9_memory_multi.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MAC_F9_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MAC_F9_SOURCES})
