
cmake_minimum_required(VERSION 3.20)

if(NOT TARGET freertos_kernel)
    message(FATAL_ERROR " freertos_addons requires freertos_kernel. Please include FreeRTOS in your project using FetchContent")
endif()

add_library(freertos_addons INTERFACE)

target_include_directories(freertos_addons INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/include>
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/include>
)

target_sources(freertos_addons INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/dlist.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/mem_pool.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/queue_simple.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/read_write_lock.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/slist.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/stack_simple.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/workqueue.c
    ${CMAKE_CURRENT_SOURCE_DIR}/c/Source/zero_copy_queue.c

    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/ccondition_variable.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cevent_groups.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cmem_pool.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cmutex.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cqueue.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cread_write_lock.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/csemaphore.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/ctasklet.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cthread.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/ctickhook.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/ctimer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/c++/Source/cworkqueue.cpp
)

target_link_libraries(freertos_addons INTERFACE freertos_kernel)
