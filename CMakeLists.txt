#
#  CMakeLists.txt
#  <Core>
#
#
#  Created by Jannis Sauer on 2026-02-17.
#

set(MAIN_DIRS
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Inc

    CACHE INTERNAL
        "the main include directories"
)

set(MAIN_SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/stm32f4xx_hal_msp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/stm32f4xx_it.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/syscalls.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/sysmem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/Src/system_stm32f4xx.c
    ${CMAKE_CURRENT_SOURCE_DIR}/startup_stm32f401xc.s

    CACHE INTERNAL
        "the main sources"
)

target_sources(${MAIN_TARGET_NAME}
    PRIVATE
        ${MAIN_SRCS}
)

target_include_directories(${MAIN_TARGET_NAME}
    PUBLIC
        ${CMAKE_BINARY_DIR}/generated
        ${MAIN_DIRS}
)

target_link_libraries(${MAIN_TARGET_NAME}
    PRIVATE
        HAL_LIB
)