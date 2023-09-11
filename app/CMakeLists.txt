set(APP_HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/Window.hpp")
set(APP_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/Window.cpp"
                "${CMAKE_CURRENT_SOURCE_DIR}/main.cpp")

add_executable(${EXECUTABLE_NAME} ${APP_SOURCES})
target_link_libraries(${EXECUTABLE_NAME} SDL3::SDL3)

if(${ENABLE_WARNINGS})
    target_set_warnings(
        TARGET
        ${EXECUTABLE_NAME}
        ENABLE
        ${ENABLE_WARNINGS}
        AS_ERRORS
        ${ENABLE_WARNINGS_AS_ERRORS})
endif()

if(${ENABLE_LTO})
    target_enable_lto(
        TARGET
        ${EXECUTABLE_NAME}
        ENABLE
        ON)
endif()

if(${ENABLE_CLANG_TIDY})
    add_clang_tidy_to_target(${EXECUTABLE_NAME})
endif()
