set(MATH_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/rand_prime.c
    ${CMAKE_CURRENT_SOURCE_DIR}/radix_to_bin.c
    ${CMAKE_CURRENT_SOURCE_DIR}/gmp_desc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tfm_desc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rand_bn.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ltm_desc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/fp/ltc_ecc_fp_mulmod.c
)

#-----------------------------------------------------------------------------
# MATH
#-----------------------------------------------------------------------------
add_library(math_shared_obj OBJECT
    ${MATH_SOURCES}
)

add_library(math_static_obj OBJECT
    ${MATH_SOURCES}
)

set_target_properties(math_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
