set(TEST_TARGET_NAME _test)
add_executable(${TEST_TARGET_NAME} 
  hello.cxx
)

target_link_libraries(${TEST_TARGET_NAME}
  ${TARGET_NAME_LIB}
  CONAN_PKG::catch2
)
target_include_directories(${TEST_TARGET_NAME} PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_SOURCE_DIR}
)

add_test(NAME ${TEST_TARGET_NAME}
  COMMAND ${TEST_TARGET_NAME} -r junit
) 


target_compile_definitions(${TEST_TARGET_NAME} PRIVATE
#  "$<$<CONFIG:DEBUG>:DEBUG>"
#  _LIBCPP_ENABLE_CXX20_REMOVED_TYPE_TRAITS
# LOG_CO_SPAWN_PRINT_EXCEPTIONS
# LOG_FOR_STATE_MACHINE
# LOG_MY_WEBSOCKET
BOOST_ASIO_ENABLE_HANDLER_TRACKING
)