cmake_minimum_required(VERSION 3.22.0)

set(HEADER_FILES
	src/d3dx12.h
	src/DXSample.h
	src/DXSampleHelper.h
	src/stdafx.h
	src/Win32Application.h
	src/D3D12HelloTriangle.h
)
set(SRC_FILES 
	src/DXSample.cpp
	src/stdafx.cpp
	src/Win32Application.cpp
	src/D3D12HelloTriangle.cpp
	src/main.cpp
)

add_executable(project1 WIN32 ${HEADER_FILES} ${SRC_FILES})

target_link_libraries(project1 
	d3d12.lib
	dxgi.lib
	d3dcompiler.lib
)

# add defines
add_definitions(-DUNICODE -D_UNICODE)

message(${CMAKE_COMMAND})
message(${CMAKE_CURRENT_BINARY_DIR})
# move shader files to output dir 
add_custom_command(
	TARGET project1 POST_BUILD
	COMMAND ${CMAKE_COMMAND} -E copy
			${CMAKE_CURRENT_SOURCE_DIR}/src/shaders.hlsl
			${CMAKE_CURRENT_BINARY_DIR}/shaders.hlsl
)