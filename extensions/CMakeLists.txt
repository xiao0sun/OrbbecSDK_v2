# Copyright (c) Orbbec Inc. All Rights Reserved.
# Licensed under the MIT License.

cmake_minimum_required(VERSION 3.10)

add_custom_target(extensions ALL)

add_custom_command(
    TARGET extensions
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory "${CMAKE_CURRENT_LIST_DIR}/filters/${OB_CURRENT_OS}" "${OB_RESOURCES_OUTPUT_DIRECTORY}/extensions/filters")

add_custom_command(
    TARGET extensions
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory "${CMAKE_CURRENT_LIST_DIR}/frameprocessor/${OB_CURRENT_OS}" "${OB_RESOURCES_OUTPUT_DIRECTORY}/extensions/frameprocessor")

set(OB_DEPTHENGINE_EXTENSION_DIR "${CMAKE_CURRENT_LIST_DIR}/depthengine/${OB_CURRENT_OS}")

if(EXISTS "${OB_DEPTHENGINE_EXTENSION_DIR}")
    add_custom_command(
        TARGET extensions
        POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory "${OB_DEPTHENGINE_EXTENSION_DIR}" "${OB_RESOURCES_OUTPUT_DIRECTORY}/extensions/depthengine")
endif()

add_custom_command(
    TARGET extensions
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory "${CMAKE_CURRENT_LIST_DIR}/firmwareupdater/${OB_CURRENT_OS}" "${OB_RESOURCES_OUTPUT_DIRECTORY}/extensions/firmwareupdater")

set_target_properties(extensions PROPERTIES FOLDER "modules")

if(OB_IS_MAIN_PROJECT)

    install(DIRECTORY "${CMAKE_CURRENT_LIST_DIR}/filters/${OB_CURRENT_OS}/" DESTINATION "${OB_EXTENSIONS_INSTALL_RPEFIX}/extensions/filters")

    install(DIRECTORY "${CMAKE_CURRENT_LIST_DIR}/frameprocessor/${OB_CURRENT_OS}/" DESTINATION "${OB_EXTENSIONS_INSTALL_RPEFIX}/extensions/frameprocessor")

if(EXISTS "${OB_DEPTHENGINE_EXTENSION_DIR}")
    install(DIRECTORY "${OB_DEPTHENGINE_EXTENSION_DIR}/" DESTINATION "${OB_EXTENSIONS_INSTALL_RPEFIX}/extensions/depthengine")
endif()

    install(DIRECTORY "${CMAKE_CURRENT_LIST_DIR}/firmwareupdater/${OB_CURRENT_OS}/" DESTINATION "${OB_EXTENSIONS_INSTALL_RPEFIX}/extensions/firmwareupdater")

endif()
