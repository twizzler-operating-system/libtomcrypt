set(MODE_OFB_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_getiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ofb_setiv.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_OFB_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_OFB_SOURCES})
