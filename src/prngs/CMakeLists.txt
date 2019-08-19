set(PRNGS_SOURCES
    sprng.c
#     sober128.c
#     rc4.c
    rng_get_bytes.c
    rng_make_prng.c
#     chacha20.c
#     fortuna.c
#     yarrow.c
)

#-----------------------------------------------------------------------------
# PRNGS
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${PRNGS_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PRNGS_SOURCES})
