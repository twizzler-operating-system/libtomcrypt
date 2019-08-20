set(MODE_F8_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_setiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_test_mode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/f8_getiv.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_F8_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_F8_SOURCES})
