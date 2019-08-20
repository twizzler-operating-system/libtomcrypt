set(PK_ASN1_DER_GENERALIZEDTIME_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_generalizedtime.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_generalizedtime.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_generalizedtime.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_GENERALIZEDTIME_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_GENERALIZEDTIME_SOURCES})
