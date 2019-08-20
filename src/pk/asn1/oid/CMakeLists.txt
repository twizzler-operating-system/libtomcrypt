set(PK_ASN1_OID_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/pk_get_oid.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pk_oid_cmp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pk_oid_str.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_OID_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_OID_SOURCES})
