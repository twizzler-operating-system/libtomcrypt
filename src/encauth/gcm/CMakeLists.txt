set(ENCAUTH_GCM_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_add_aad.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_add_iv.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_gf_mult.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_mult_h.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_process.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_reset.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gcm_test.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${ENCAUTH_GCM_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${ENCAUTH_GCM_SOURCES})
