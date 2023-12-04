cmake_minimum_required(VERSION 3.26)

project(SileroVadOnnx)

add_executable(SileroVadOnnx
        silero-vad-onnx.cpp)
target_compile_features(SileroVadOnnx PUBLIC cxx_std_17)

target_include_directories(SileroVadOnnx PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/onnxruntime-osx-arm64-1.16.3/include)

add_library(onnxruntime SHARED IMPORTED)

set_target_properties(onnxruntime PROPERTIES IMPORTED_LOCATION
        ${CMAKE_CURRENT_SOURCE_DIR}/onnxruntime-osx-arm64-1.16.3/lib/libonnxruntime.dylib)

target_link_libraries(SileroVadOnnx PRIVATE
        onnxruntime
)

