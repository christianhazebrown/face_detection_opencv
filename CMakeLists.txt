cmake_minimum_required(VERSION 3.10)
project(test)
find_package(OpenCV REQUIRED)
add_executable(test src/main.cpp src/FaceDetector.cpp)
target_link_libraries(test ${OpenCV_LIBS})
target_include_directories(${PROJECT_NAME} PRIVATE include)

# Introduce preprocessor variables to keep paths of asset files 
set(FACE_DETECTION_CONFIGURATION "${PROJECT_SOURCE_DIR}/assets/deploy.prototxt")
set(FACE_DETECTION_WEIGHTS "${PROJECT_SOURCE_DIR}/assets/res10_300x300_ssd_iter_140000_fp16.caffemodel")  
target_compile_definitions(${PROJECT_NAME} PRIVATE  FACE_DETECTION_CONFIGURATION="${FACE_DETECTION_CONFIGURATION}")  
target_compile_definitions(${PROJECT_NAME} PRIVATE  FACE_DETECTION_WEIGHTS="${FACE_DETECTION_WEIGHTS}")