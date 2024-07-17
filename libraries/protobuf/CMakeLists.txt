PROJECT(rpc)
CMAKE_MINIMUM_REQUIRED (VERSION 3.0.0)
SET(CMAKE_CXX_FLAGS "-g -Wall -std=c++11")

# Define an empty LIBS variable
set(PROTO_LIBS)

# Read the lib files from the text file and append to the LIBS variable
file(STRINGS "C:/Users/rizzo/OneDrive/Desktop/lib_files_list.txt" lib_files)
list(APPEND PROTO_LIBS ${lib_files})

find_package(Protobuf REQUIRED)

ADD_SUBDIRECTORY(proto)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})
INCLUDE_DIRECTORIES(${Protobuf_INCLUDE_DIRS})
ADD_EXECUTABLE(main main.cpp)
TARGET_LINK_LIBRARIES(main proto ${Protobuf_LIBRARIES})
TARGET_LINK_LIBRARIES(main proto ${PROTO_LIBS})
