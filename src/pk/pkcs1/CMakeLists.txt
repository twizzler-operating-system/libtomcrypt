set(PK_PKCS1_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_mgf1.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_oaep_encode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_v1_5_decode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_v1_5_encode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_pss_encode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_pss_decode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_oaep_decode.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_os2ip.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs_1_i2osp.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_PKCS1_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_PKCS1_SOURCES})
