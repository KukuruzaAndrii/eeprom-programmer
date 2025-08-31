cmake_minimum_required(VERSION 3.13)

if(NOT DEFINED PICO_SDK_PATH)
    set(PICO_SDK_PATH "../lib/pico-sdk" CACHE PATH "Path to pico-sdk")
endif()


set(PICO_PLATFORM "rp2040" CACHE PATH "Path to pico-sdk")
set(PICO_PLATFORM "rp2040" CACHE PATH "Path to pico-sdk")

include(pico_sdk_import.cmake)

project(eeprom_programmer C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()

add_executable(eeprom_programmer
	src/main.c

)

pico_enable_stdio_usb(eeprom_programmer 1)
pico_enable_stdio_uart(eeprom_programmer 1)

pico_add_extra_outputs(eeprom_programmer)

target_link_libraries(eeprom_programmer pico_stdlib)
