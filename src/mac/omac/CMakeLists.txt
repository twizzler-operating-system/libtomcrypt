set(MAC_OMAC_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_memory_multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_file.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_process.c
    ${CMAKE_CURRENT_SOURCE_DIR}/omac_memory.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MAC_OMAC_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MAC_OMAC_SOURCES})
