#------------------------------------------------------------------------------------第一个可执行文件
set(EXEC_hello1 hello1_main) #NOTE: 这里不能和目录hello1取名一样，下面会copy错误
set(SRC_hello1 hello1.c)
add_executable(${EXEC_hello1} ${SRC_hello1})
target_link_libraries(${EXEC_hello1} ${GLIB_LIBRARY_DIRS} ${GTK3_LIBRARIES})
add_custom_command(TARGET ${EXEC_hello1}
                   POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E
		   copy $<TARGET_FILE:${EXEC_hello1}> ${PROJECT_BINARY_DIR})
set_property(DIRECTORY PROPERTY
             ADDITIONAL_MAKE_CLEAN_FILES ${PROJECT_BINARY_DIR}/hello1_main)

#------------------------------------------------------------------------------------第二个可执行文件
set(EXEC_hello2 hello2_main)
set(SRC_hello2 hello2.c)
add_executable(${EXEC_hello2} ${SRC_hello2})
target_link_libraries(${EXEC_hello2} ${GLIB_LIBRARY_DIRS} ${GTK3_LIBRARIES})
add_custom_command(TARGET ${EXEC_hello2}
                   POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E
		   copy $<TARGET_FILE:${EXEC_hello2}> ${PROJECT_BINARY_DIR})
set_property(DIRECTORY PROPERTY
             ADDITIONAL_MAKE_CLEAN_FILES ${PROJECT_BINARY_DIR}/hello2_main)

#------------------------------------------------------------------------------------第三个可执行文件
set(EXEC_button1 button1_main)
set(SRC_button1 button1.c)
add_executable(${EXEC_button1} ${SRC_button1})
target_link_libraries(${EXEC_button1} ${GLIB_LIBRARY_DIRS} ${GTK3_LIBRARIES})
add_custom_command(TARGET ${EXEC_button1}
                   POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E
		   copy $<TARGET_FILE:${EXEC_button1}> ${PROJECT_BINARY_DIR})
set_property(DIRECTORY PROPERTY
             ADDITIONAL_MAKE_CLEAN_FILES ${PROJECT_BINARY_DIR}/button1_main)
