SUBDIRS = .

bin_PROGRAMS = rtbxegen_exchange_runner

rtbxegen_exchange_runner_SOURCES = \
    exchange_request_handler.cpp \
    openrtb_request_handler.cpp \
    realtime-bidding.pb.cc \
    adx_request_handler.cpp \
    smaato_request_handler.cpp \
    rtbxegen_exchange_runner.cpp

rtbxegen_exchange_runner_LDADD = -lproxygenhttpserver -lfolly -lglog -lgflags -lprotobuf \
    ../../lib/proxygen/libproxygen_rtbxegen.la \
    ../../lib/openrtb/libopenrtb_rtbxegen.la \
    ../../lib/common/libcommon_rtbxegen.la

rtbxegen_exchange_runner_LDFLAGS = -pthread