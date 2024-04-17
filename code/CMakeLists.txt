cmake_minimum_required(VERSION 3.16.0)

list(APPEND EXTRA_COMPONENT_DIRS $ENV{IDF_PATH}/examples/common_components/protocol_examples_common components/esp-tflite-micro components/jomjol_helper)

#set(COMPONENT_DIRS $ENV{IDF_PATH}/components components components/esp-tflite-micro)
#set(CMAKE_CURRENT_LIST_DIR /home/sant/tesis/tesis-code-analisys/code/main)
#$ENV{IDF_PATH}/components/
#set(COMPONENTS
#    esp_pm
#    esp_wifi
#    esp_event
#    esp_netif
#    nvs_flash
#    main
#)

#ADD_CUSTOM_COMMAND(
#    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/version.cpp
#           ${CMAKE_CURRENT_BINARY_DIR}/_version.cpp
#    COMMAND ${CMAKE_COMMAND} -P
#            ${CMAKE_CURRENT_SOURCE_DIR}/version.cmake)

if(EXISTS "${SDKCONFIG}.defaults")
    if(EXISTS "sdkconfig.defaults")
        set(SDKCONFIG_DEFAULTS "${SDKCONFIG}.defaults;sdkconfig.defaults")
        message(STATUS "-- Using defaults: ${SDKCONFIG_DEFAULTS} + sdkconfig.defaults")
    else()
        set(SDKCONFIG_DEFAULTS "${SDKCONFIG}.defaults")
    endif()
    message(STATUS "-- Using defaults: ${SDKCONFIG_DEFAULTS}")
endif()

include($ENV{IDF_PATH}/tools/cmake/project.cmake)

idf_build_set_property(CXX_COMPILE_OPTIONS "-fpermissive" APPEND)
#component_compile_options("-fpermissive")

project(AI-on-the-edge)
