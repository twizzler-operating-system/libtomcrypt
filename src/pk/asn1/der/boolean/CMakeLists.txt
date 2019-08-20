set(PK_ASN1_DER_BOOLEAN_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_boolean.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_boolean.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_boolean.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_BOOLEAN_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_BOOLEAN_SOURCES})
