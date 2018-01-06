CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

INCLUDE_DIRECTORIES(${EXTERNAL_INSTALL_LOCATION}/include)
LINK_DIRECTORIES(${EXTERNAL_INSTALL_LOCATION}/lib)

foreach(subdir example)
  SET(test_target "${subdir}_test")
  SET(test_src "${subdir}/main.cc")
  ADD_EXECUTABLE(${test_target} ${test_src})
  TARGET_LINK_LIBRARIES(${test_target} mylib gtest gtest_main pthread)
  ADD_TEST(NAME ${subdir} COMMAND $<TARGET_FILE:${test_target}>)
endforeach(subdir)

