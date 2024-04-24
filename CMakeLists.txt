project(apdu_lib)

set(CMAKE_CXX_STANDARD 20)
FILE(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
FILE(GLOB_RECURSE HEADER_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.h)
find_path(nfc_include_dir nfc/nfc.h)
find_library(nfc_lib nfc)

add_library(${PROJECT_NAME} STATIC ${SRC_FILES} ${HEADER_FILES})
target_link_libraries(apdu_lib ${nfc_lib})
target_include_directories(apdu_lib PUBLIC ${nfc_include_dir})
target_include_directories(apdu_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
include_directories(nfc/include)