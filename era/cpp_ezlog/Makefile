link = ld
cpp = c++
hpp = ../hpp/
lib = ../lib/
logger = ../cpp_logger/
ezlog = ../cpp_ezlog/
zstring = ../cpp_zstring/
opts = -std=c++14 -I$(hpp)

all: ezlog.run tezlog.run 

posix: ezlog

windows: ezlog.exe

# ::::: Target: tezlog.run ::::: 
tezlog.run: tezlog.o libera.a
	$(cpp) $(opts) -o tezlog.run tezlog.o -L$(lib) -lera
	exec "./tezlog.run"

ezlog.run: ezcon.o libera.a
	$(cpp) $(opts) -o ezlog.run ezcon.o -L$(lib) -lera
	exec "./ezlog.run"

# Use zClassic ".ezlog" file in POSIX:
ezlog: ezcon.o libera.a
	$(cpp) $(opts) -o ezlog ezcon.o -L$(lib) -lera

# Use zClassic ".ezlog" file on Microsoft's Windows:
ezlog.exe: ezcon.o libera.a
	$(cpp) $(opts) -o ezlog.exe ezcon.o -L$(lib) -lera

tezlog.o: $(ezlog)tezlog.cpp
	$(cpp) $(opts) -c $(ezlog)tezlog.cpp

ezcon.o: $(ezlog)ezcon.cpp $(hpp)EzLog.hpp
	$(cpp) $(opts) -c $(ezlog)ezcon.cpp

# ::::: GNU-Style Library :::::
libera.a:
	cd ../lib && $(MAKE) 

# sudo apt-get install clang-format
format:
	find . -type f -name "*.hpp" -exec clang-format -style=Chromium -i "{}" ";"
	find . -type f -name "*.cpp" -exec clang-format -style=Chromium -i "{}" ";"

clean:
	rm -f *.o
	rm -f *.a
	rm -f *.run
	rm -f ezlog
	rm -f .ezlog
	rm -f ezlog.exe
	rm -f *.out
	rm -f *.log
	chmod 666 *.?pp

