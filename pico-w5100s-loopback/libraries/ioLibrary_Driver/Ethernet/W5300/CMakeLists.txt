add_library(W5100S_FILES STATIC
        w5300.c
        w5300.h
        )

target_include_directories(W5100S_FILES PUBLIC
        ../../Ethernet
        )

target_link_libraries(W5100S_FILES PUBLIC
        pico_stdlib
        ETHERNET_FILES
        )