add_library(
    doctest
    INTERFACE
)
target_sources(
    doctest
    INTERFACE
    ${PROJECT_SOURCE_DIR}/include/doctest/doctest.h
)
target_include_directories(
    doctest
    INTERFACE
    ${PROJECT_SOURCE_DIR}/include/bigWigs2tensors
)

add_executable(
   test
   main.cc
   ${PROJECT_SOURCE_DIR}/include/bigWigs2tensors/util.h
   ${PROJECT_SOURCE_DIR}/src/util.cc
)
target_include_directories(test PUBLIC ${CMAKE_SOURCE_DIR}/include ../extern/libBigWig)
target_link_libraries(test libBigWig torch doctest bigWigs2tensors_lib)

#add_executable(
#    test_no_doctest
#    main_no_doctest.cc
#    ${PROJECT_SOURCE_DIR}/include/bigWigs2tensors/util.h
#    ${PROJECT_SOURCE_DIR}/src/util.cc
#)
#target_include_directories(test_no_doctest PUBLIC ${CMAKE_SOURCE_DIR}/include ../extern/libBigWig)
#target_link_libraries(test_no_doctest libBigWig torch lib${PROJECT_NAME})