set(PK_ASN1_DER_GENERAL_SOURCES
    der_length_asn1_identifier.c
    der_encode_asn1_length.c
    der_asn1_maps.c
    der_decode_asn1_length.c
    der_length_asn1_length.c
    der_encode_asn1_identifier.c
    der_decode_asn1_identifier.c
)

#-----------------------------------------------------------------------------
# ASN1 DER GENERAL
#-----------------------------------------------------------------------------
add_library(pk_asn1_der_general_shared_obj OBJECT
    ${PK_ASN1_DER_GENERAL_SOURCES}
)

add_library(pk_asn1_der_general_static_obj OBJECT
    ${PK_ASN1_DER_GENERAL_SOURCES}
)

set_target_properties(pk_asn1_der_general_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
