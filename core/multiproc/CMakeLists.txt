############################################################################
# CMakeLists.txt file for building ROOT core/multiproc package
############################################################################

set(headers TMPClient.h MPSendRecv.h ROOT/TProcessExecutor.hxx TProcPool.h TMPWorker.h TPoolWorker.h TPoolProcessor.h TPoolPlayer.h MPCode.h PoolUtils.h)

set(sources TMPClient.cxx MPSendRecv.cxx TProcessExecutor.cxx TMPWorker.cxx TPoolPlayer.cxx)

ROOT_GENERATE_DICTIONARY(G__MultiProc ${headers} MODULE MultiProc LINKDEF LinkDef.h)

ROOT_OBJECT_LIBRARY(MultiProcObjs ${sources} G__MultiProc.cxx)
ROOT_LINKER_LIBRARY(MultiProc $<TARGET_OBJECTS:MultiProcObjs> DEPENDENCIES Core Net TreePlayer dl)
ROOT_INSTALL_HEADERS()
