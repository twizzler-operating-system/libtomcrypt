set(PK_ASN1_DER_INTEGER_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_integer.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_integer.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_integer.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_INTEGER_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_INTEGER_SOURCES})
