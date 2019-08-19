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
target_sources(${PROJECT_NAME}-shared PRIVATE ${MATH_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MATH_SOURCES})
