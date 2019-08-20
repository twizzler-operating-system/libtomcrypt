set(MODE_XTS_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_mult_x.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xts_done.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_XTS_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_XTS_SOURCES})
