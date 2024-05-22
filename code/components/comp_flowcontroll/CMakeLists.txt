FILE(GLOB_RECURSE app_sources ${CMAKE_CURRENT_SOURCE_DIR}/*.*)

idf_component_register(SRCS ${app_sources}
                    INCLUDE_DIRS "."
                    REQUIRES esp_timer esp_wifi comp_tfliteclass comp_helper comp_controlcamera comp_fileserver comp_image_proc comp_wlan)


