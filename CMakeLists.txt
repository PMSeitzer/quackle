cmake_minimum_required (VERSION 3.10)

project (libquackle)

message("-- Configuring libquackle")

include("${CMAKE_CURRENT_SOURCE_DIR}/Settings.cmake")

find_package(Threads REQUIRED)

set(CMAKE_CXX_STANDARD 11)

SET(CMAKE_CXX_COMPILER "/usr/local/opt/llvm/bin/clang++")

#Isuse 109: use openmp library
set(CMAKE_CXX_FLAGS "-fopenmp")

# Necessary for Qt Creator
# commenting out causes linker error:
#
# ld: library not found for -lomp
#
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L/usr/local/opt/llvm/lib/")

# Necessary for Qt Creator
#
# without this, cannot find std libraries
#
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -I/usr/local/opt/llvm/include/c++/v1/")

set(LIBQUACKLE_SOURCES
	alphabetparameters.cpp
	bag.cpp
	board.cpp
	boardparameters.cpp
	bogowinplayer.cpp
	catchall.cpp
	clock.cpp
	computerplayer.cpp
	computerplayercollection.cpp
	datamanager.cpp
	endgame.cpp
	endgameplayer.cpp
	enumerator.cpp
	evaluator.cpp
	game.cpp
	gameparameters.cpp
	generator.cpp
	lexiconparameters.cpp
	move.cpp
	player.cpp
	playerlist.cpp
	preendgame.cpp
	rack.cpp
	reporter.cpp
	resolvent.cpp
	sim.cpp
	strategyparameters.cpp
)

set(LIBQUACKLE_HEADERS
	alphabetparameters.h
	bag.h
	board.h
	boardparameters.h
	bogowinplayer.h
	catchall.h
	clock.h
	computerplayer.h
	computerplayercollection.h
	datamanager.h
	endgame.h
	endgameplayer.h
	enumerator.h
	evaluator.h
	fixedstring.h
	gaddag.h
	game.h
	gameparameters.h
	generator.h
	lexiconparameters.h
	move.h
	player.h
	playerlist.h
	preendgame.h
	rack.h
	reporter.h
	resolvent.h
	sim.h
	strategyparameters.h
	uv.h
)

add_library(libquackle
	${LIBQUACKLE_SOURCES} ${LIBQUACKLE_HEADERS}
)

target_link_libraries(libquackle Threads::Threads)
