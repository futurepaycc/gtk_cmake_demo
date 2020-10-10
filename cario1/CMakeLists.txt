pkg_check_modules(CARIO REQUIRED)
include_directories(${CARIO_INCLUDE_DIRS})
link_directories(${CARIO_LIBRARY_DIRS})
add_definitions(${CARIO_CFLAGS_OTHER})

set(EXEC cario1_main) #NOTE: 这里不能和目录hello1取名一样，下面会copy错误
set(SRC_LIST hello1.c)
add_executable(${EXEC} ${SRC_LIST})

# Link the main target
target_link_libraries(${EXEC} ${GLIB_LIBRARY_DIRS} ${GTK3_LIBRARIES} ${CARIO_LIBRARIES} -lm)

# Copy final executable in build root directory
add_custom_command(TARGET ${EXEC}
                   POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E
		   copy $<TARGET_FILE:${EXEC}> ${PROJECT_BINARY_DIR})
# # Cleaning it: 这里只是增加一个make clean的目标
set_property(DIRECTORY PROPERTY
             ADDITIONAL_MAKE_CLEAN_FILES ${PROJECT_BINARY_DIR}/cario1_main)
