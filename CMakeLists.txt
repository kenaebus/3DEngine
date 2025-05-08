# CMakeList.txt : CMake project for 3DEngine, include source and define
# project specific logic here.
#
cmake_minimum_required(VERSION 3.10)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("3DEngine")

# Find vckpg packages
find_package(fmt CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(glad CONFIG REQUIRED)

# Add source to this project's executable.
add_executable (3DEngine "3DEngine.cpp" "3DEngine.h")


if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET 3DEngine PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
target_link_libraries(3DEngine PRIVATE fmt::fmt glfw glad::glad)


