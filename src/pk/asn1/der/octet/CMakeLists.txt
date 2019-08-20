set(PK_ASN1_DER_OCTET_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_octet_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_octet_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_octet_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_OCTET_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_OCTET_SOURCES})
