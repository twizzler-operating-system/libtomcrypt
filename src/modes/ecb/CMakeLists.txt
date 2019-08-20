set(MODE_ECB_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/ecb_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ecb_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ecb_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ecb_decrypt.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_ECB_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_ECB_SOURCES})
