set(MODE_CBC_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_setiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cbc_getiv.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_CBC_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_CBC_SOURCES})
