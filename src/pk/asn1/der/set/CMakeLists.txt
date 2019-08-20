set(PK_ASN1_DER_SET_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_setof.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_set.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_SET_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_SET_SOURCES})
