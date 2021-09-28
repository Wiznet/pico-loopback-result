add_executable(w5x00_loopback
        w5x00_loopback.c
        )

target_include_directories(w5x00_loopback PUBLIC
        ${CMAKE_SOURCE_DIR}/libraries/ioLibrary_Driver/Application/loopback
        ${CMAKE_SOURCE_DIR}/libraries/ioLibrary_Driver/Ethernet
        ${CMAKE_SOURCE_DIR}/libraries/ioLibrary_Driver/Ethernet/W5100S
        )

target_link_libraries(w5x00_loopback PUBLIC
        pico_stdlib
        hardware_spi
        hardware_dma
        LOOPBACK_FILES
        ETHERNET_FILES
        W5100S_FILES
        )

pico_enable_stdio_usb(w5x00_loopback 1)
pico_enable_stdio_uart(w5x00_loopback 0)

pico_add_extra_outputs(w5x00_loopback)
