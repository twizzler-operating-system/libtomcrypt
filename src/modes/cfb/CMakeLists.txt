set(MODE_CFB_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_getiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cfb_setiv.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_CFB_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_CFB_SOURCES})
