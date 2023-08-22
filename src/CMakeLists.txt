project(qamqp)

set(PRIVATE_HEADERS
	qamqpchannel_p.h
	qamqpchannelhash_p.h
	qamqpclient_p.h
	qamqpexchange_p.h
	qamqpframe_p.h
	qamqpmessage_p.h
	qamqpqueue_p.h
)

set(INSTALL_HEADERS
	qamqpauthenticator.h
	qamqpchannel.h
	qamqpclient.h
	qamqpexchange.h
	qamqpglobal.h
	qamqpmessage.h
	qamqpqueue.h
	qamqptable.h
	qamqp.h
)

set(HEADERS
	${INSTALL_HEADERS}
	${PRIVATE_HEADERS}
)

set(SOURCES
	qamqpauthenticator.cpp
	qamqpchannel.cpp
	qamqpchannelhash.cpp
	qamqpclient.cpp
	qamqpexchange.cpp
	qamqpframe.cpp
	qamqpmessage.cpp
	qamqpqueue.cpp
	qamqptable.cpp
)

if(Qt6_FOUND)
qt_add_library(${PROJECT_NAME} SHARED
	${HEADERS}
	${SOURCES}
)
else()
add_library(${PROJECT_NAME} SHARED
	${HEADERS}
	${SOURCES}
)
endif()

target_compile_definitions(${PROJECT_NAME} PRIVATE
	QAMQP_BUILD
	QAMQP_SHARED
)

target_link_libraries(${PROJECT_NAME} PRIVATE
	Qt::Core
	Qt::Network
)

