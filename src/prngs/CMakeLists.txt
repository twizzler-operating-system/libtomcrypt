set(PRNGS_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/sprng.c
    ${CMAKE_CURRENT_SOURCE_DIR}/sober128.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rng_get_bytes.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rng_make_prng.c
    ${CMAKE_CURRENT_SOURCE_DIR}/chacha20.c
    ${CMAKE_CURRENT_SOURCE_DIR}/fortuna.c
    ${CMAKE_CURRENT_SOURCE_DIR}/yarrow.c
)

#-----------------------------------------------------------------------------
# PRNGS
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${PRNGS_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PRNGS_SOURCES})
