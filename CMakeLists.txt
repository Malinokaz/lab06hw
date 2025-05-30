cmake_minimum_required(VERSION 3.4)

project(Solver
    VERSION 1.0.0
    DESCRIPTION "Equation Solver Application"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(MSVC)
    add_compile_options(/W4 /WX)
else()
    add_compile_options(-Wall -Wextra -pedantic -Werror)
endif()


set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/artifacts)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/artifacts)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/artifacts)


add_subdirectory(solver_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(formatter_lib)


set(CPACK_PACKAGE_NAME "${PROJECT_NAME}")
set(CPACK_PACKAGE_VERSION "${PROJECT_VERSION}")
set(CPACK_PACKAGE_DESCRIPTION "Equation solver app")
set(CPACK_PACKAGE_VENDOR "Vladimir")
set(CPACK_PACKAGE_CONTACT "malinokaz@ya.ru")

if(WIN32)
    set(CPACK_GENERATOR "TGZ;ZIP;NSIS")
elseif(APPLE)
    set(CPACK_GENERATOR "TGZ;ZIP;DragNDrop")
else()
    set(CPACK_GENERATOR "TGZ;ZIP;DEB;RPM")
endif()

include(CPack)
