set(MODE_CTR_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_getiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_setiv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_start.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ctr_decrypt.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MODE_CTR_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MODE_CTR_SOURCES})
