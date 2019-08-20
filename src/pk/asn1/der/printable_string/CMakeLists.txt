set(PK_ASN1_DER_PRINTABLE_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_printable_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_printable_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_printable_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_PRINTABLE_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_PRINTABLE_SOURCES})
