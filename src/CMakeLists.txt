CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

FILE(GLOB sources *.cc)
list(REMOVE_ITEM sources "main.cc")
ADD_LIBRARY(mylib ${sources})

ADD_EXECUTABLE(main main.cc)
TARGET_LINK_LIBRARIES(main mylib)

