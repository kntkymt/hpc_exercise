PROGRAM=image_processing
OBJS=utils/image.o utils/image_util.o main.o

CC = g++
CXXFLAGS=-lm -std=c++0x -fopenmp -march=native -Wno-unused-result -mfpmath=both -O3 -mtune=native

.SUFFIXES: .cpp .o

.PHONY: all
all: depend $(PROGRAM)

$(PROGRAM): $(OBJS)
	$(CC) $(CXXFLAGS) -o $(PROGRAM) $^

.c.o:
	$(CC) $(CXXFLAGS) -c $<

.PHONY: clean
clean:
	$(RM) $(PROGRAM) $(OBJS) depend.inc *.ppm *.pgm

.PHONY: depend
depend: $(OBJS:.o=.cpp)
	-@ $(RM) depend.inc
	-@ for i in $^; do cpp -MM $$i | sed "s/\ [_a-zA-Z0-9][_a-zA-Z0-9]*\.cpp//g" >> depend.inc; done

-include depend.inc
