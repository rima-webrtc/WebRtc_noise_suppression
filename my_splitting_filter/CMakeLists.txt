cmake_minimum_required(VERSION 3.10)
project(test_48k)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "-g") # 调试信息 set(CMAKE_CXX_FLAGS "-Wall") # 开启所有警告
set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS}  -fPIC -O0 -Wall -g2 -ggdb")
add_deFinitions(-DWEBRTC_POSIX)

include_directories(rtc_base/.)
include_directories(splitting_filter/.)
include_directories(AduioFile/.)

aux_source_directory(rtc_base/. rtc_base)
aux_source_directory(splitting_filter/. splitting_filter)
aux_source_directory(AduioFile/. AduioFile)
#aux_source_directory(include/rtc_base/.rtc_base)
#aux_source_directory(include/splitting_filter/. splitting_filter)


add_executable(my_splitting_filter
test.cc
${rtc_base}
${AduioFile}
${splitting_filter}
)

