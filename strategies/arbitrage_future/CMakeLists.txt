project(arbitrage_future)
if(CMAKE_SYSTEM_NAME MATCHES "Linux")
    message(${PROJECT_SOURCE_DIR})
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,-Bsymbolic")
    set(BOOST_THREAD "boost_thread-mt")
else()
    set(BOOST_THREAD "boost_thread")
endif()

message("[${PROJECT_NAME}]project source dir: ${PROJECT_SOURCE_DIR}")
message("[${PROJECT_NAME}]libs: ${libs}")

add_library(arbitrage_future SHARED "${PROJECT_SOURCE_DIR}/arbitrage_future.cpp" "${PROJECT_SOURCE_DIR}/../arbitrage_base_future.cpp")
target_link_libraries(arbitrage_future ${libs})
set_target_properties(arbitrage_future PROPERTIES PREFIX "strategy_")
install (TARGETS arbitrage_future DESTINATION bin/strategies)
