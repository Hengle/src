
set(SHARED_SOURCES
    shared/CentralServerConnection.cpp
    shared/CentralServerConnection.h
    shared/ChatServerConnection.cpp
    shared/ChatServerConnection.h
    shared/ConfigCustomerServiceServer.cpp
    shared/ChatServerConnection.cpp
    shared/ChatServerConnection.h
    shared/ConfigCustomerServiceServer.h
    shared/ConnectionServerConnection.cpp
    shared/ConnectionServerConnection.h
    shared/CustomerServiceInterface.cpp
    shared/CustomerServiceInterface.h
    shared/CustomerServiceServer.cpp
    shared/CustomerServiceServer.h
    shared/CustomerServiceServerMetricsData.cpp
    shared/CustomerServiceServerMetricsData.h
    shared/FirstCustomerServiceServer.cpp
    shared/FirstCustomerServiceServer.h
    shared/GameServerConnection.cpp
    shared/GameServerConnection.h
)

if(WIN32)
	set(PLATFORM_SOURCES "")
else()
	set(PLATFORM_SOURCES
		linux/main.cpp
	)
endif()

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/shared
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedCompression/include/public
	${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedDebug/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedFile/include/public
	${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedFoundation/include/public
	${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedFoundationTypes/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedLog/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedMath/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedMathArchive/include/public
	
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedMessageDispatch/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedNetwork/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedNetworkMessages/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedRandom/include/public
    ${SWG_ENGINE_SOURCE_DIR}/shared/library/sharedThread/include/public
    ${SWG_ENGINE_SOURCE_DIR}/server/library/serverMetrics/include/public
    ${SWG_ENGINE_SOURCE_DIR}/server/library/serverNetworkMessages/include/public
    ${SWG_ENGINE_SOURCE_DIR}/server/library/serverUtility/include/public
	${SWG_EXTERNALS_SOURCE_DIR}/ours/library/archive/include
    ${SWG_EXTERNALS_SOURCE_DIR}/ours/library/singleton/include
    ${SWG_EXTERNALS_SOURCE_DIR}/ours/library/unicode/include
    ${SWG_EXTERNALS_SOURCE_DIR}/ours/library/unicodeArchive/include/public
    ${SWG_EXTERNALS_SOURCE_DIR}/3rd/library/soePlatform/CSAssist/projects/CSAssist/CSAssistgameapi
    ${LIBXML2_INCLUDE_DIR}
)

add_executable(CustomerServiceServer
	${SHARED_SOURCES}
	${PLATFORM_SOURCES}
)

target_link_libraries(CustomerServiceServer
    sharedCompression
    sharedDebug
    sharedFile
    sharedFoundation
    sharedLog
    sharedMath
    
    sharedMessageDispatch
    sharedNetwork
    sharedNetworkMessages
    sharedRandom
    sharedSynchronization
    sharedThread
    sharedXml
    serverMetrics
    serverNetworkMessages
    serverUtility
    archive
    unicode
    unicodeArchive
    CSAssist
    ${CMAKE_DL_LIBS}
)
