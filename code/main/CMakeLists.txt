
string(TIMESTAMP BUILD_TIME "%Y-%m-%d %H:%M")


set(VERSION "const char* GIT_REV=\"cualquiera\";
            \nconst char* GIT_TAG=\"cualquiera\";
            \nconst char* GIT_BRANCH=\"cualquiera\";
            \nconst char* BUILD_TIME=\"cualquiera\";")

set(VERSION_HTML "1.0.0")
set(VERSION_ "")

#if (NOT "${VERSION}" STREQUAL "${VERSION_}")
#    file(WRITE ${CMAKE_CURRENT_SOURCE_DIR}/version.cpp "${VERSION}")
#    file(WRITE ${CMAKE_CURRENT_SOURCE_DIR}/../sd-card/html/version.txt "${VERSION_HTML}")
#endif()
#######################################################################
#######################################################################

#FILE(GLOB_RECURSE app_sources ${CMAKE_SOURCE_DIR}/main/*.*)
FILE(GLOB_RECURSE app_sources /home/sant/tesis/tesis-code-analisys/code/main/*.*)

# idf_component_register(SRCS ${app_sources})

#idf_component_register(SRCS ${app_sources}
#                    INCLUDE_DIRS "."
#                    REQUIRES esp_psram)

idf_component_register(
SRCS ${app_sources} 
    $ENV{IDF_PATH}/components/esp_pm 
    $ENV{IDF_PATH}/components/esp_wifi 
    $ENV{IDF_PATH}/components/esp_event
    $ENV{IDF_PATH}/components/esp_netif 
    $ENV{IDF_PATH}/components/nvs_flash 
    $ENV{IDF_PATH}/components/esp_eth
    $ENV{IDF_PATH}/components/hal
    $ENV{IDF_PATH}/components/esp_driver_ledc
INCLUDE_DIRS "." 
    #${CMAKE_SOURCE_DIR}/components
    ${CMAKE_SOURCE_DIR}/components/comp_wlan
    ${CMAKE_SOURCE_DIR}/components/comp_controlGPIO
    ${CMAKE_SOURCE_DIR}/components/comp_flowcontroll
    ${CMAKE_SOURCE_DIR}/components/comp_image_proc
    ${CMAKE_SOURCE_DIR}/components/comp_controlcamera
    ${CMAKE_SOURCE_DIR}/components/comp_fileserver
    ${CMAKE_SOURCE_DIR}/components/esp32-camera/driver/include
    ${CMAKE_SOURCE_DIR}/components/esp32-camera/conversions/include
    $ENV{IDF_PATH}/components/esp_pm/include 
    $ENV{IDF_PATH}/components/esp_wifi/include 
    $ENV{IDF_PATH}/components/esp_event/include 
    $ENV{IDF_PATH}/components/esp_netif/include 
    $ENV{IDF_PATH}/components/nvs_flash/include 
    $ENV{IDF_PATH}/components/spi_flash/include 
    $ENV{IDF_PATH}/components/esp_eth/include
    $ENV{IDF_PATH}/components/esp_http_server/include
    $ENV{IDF_PATH}/components/hal/include/
    $ENV{IDF_PATH}/components/esp_partition/include
    $ENV{IDF_PATH}/components/http_parser
    $ENV{IDF_PATH}/components/esp_driver_ledc/include
REQUIRES comp_helper esp_psram
)