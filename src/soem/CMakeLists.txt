if(WIN32)
	include_directories(
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem/osal
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem/osal/win32
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem/oshw/win32
	)
else()
	include_directories(
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem/osal
		${PROJECT_SOURCE_DIR}/include/youbot_driver/soem/oshw/linux
	)
endif()

if(WIN32)
	set(SOEM_OS_SOURCE_FILES
		osal/win32/osal.c
		oshw/win32/nicdrv.c
		oshw/win32/oshw.c
	)		
else()
	set(SOEM_OS_SOURCE_FILES
		osal/linux/osal.c
		oshw/linux/nicdrv.c
		oshw/linux/oshw.c
	)		
endif()

add_library(soem 
	ethercatbase.c 
	ethercatcoe.c 
	ethercatconfig.c 
	ethercatdc.c 
	ethercatfoe.c 
	ethercatmain.c 
	ethercatprint.c 
	ethercatsoe.c 
	${SOEM_OS_SOURCE_FILES}
)

install(TARGETS soem 
  ARCHIVE DESTINATION lib/${PROJECT_NAME}
  LIBRARY DESTINATION lib/${PROJECT_NAME}
  RUNTIME DESTINATION bin/${PROJECT_NAME}
)

