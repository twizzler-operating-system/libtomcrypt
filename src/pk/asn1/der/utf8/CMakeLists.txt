set(PK_ASN1_DER_UTF8_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_utf8_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_utf8_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_utf8_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_UTF8_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_UTF8_SOURCES})
