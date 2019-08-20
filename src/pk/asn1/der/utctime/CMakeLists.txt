set(PK_ASN1_DER_UTCTIME_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_utctime.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_utctime.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_utctime.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_UTCTIME_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_UTCTIME_SOURCES})
