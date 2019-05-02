cmake_minimum_required(VERSION 2.6)

project(purePlayTest)

include_directories("include")


  find_package(ALSA REQUIRED)
  find_package(Threads REQUIRED CMAKE_THREAD_PREFER_PTHREAD)
	include_directories(${ALSA_INCLUDE_DIR})
  list(APPEND LINKLIBS ${ALSA_LIBRARY} ${CMAKE_THREAD_LIBS_INIT})
  list(APPEND COMPILE_OPTION -D__LINUX_ALSA__)

  list(APPEND SRC
  main.cpp
  src/RtAudio.cpp
  )

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries(${PROJECT_NAME} ${LINKLIBS})
target_compile_options(${PROJECT_NAME} PRIVATE ${COMPILE_OPTION})
