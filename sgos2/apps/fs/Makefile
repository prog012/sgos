#sgos module

CXXFLAGS = -g -Werror -I../../include/c++ -I../../include -nostdlib -fleading-underscore --no-exceptions
CCFLAGS = -g -Werror -I../../include -nostdlib -fno-builtin -fleading-underscore
LDFLAGS = -shared 
ODFLAGS = -S

#here defines the program information
PROGRAM = filesystem
LDFLAGS += ../../crt/crt.a ../../api/api.a

CXX = g++ $(CXXFLAGS)
CC = gcc $(CCFLAGS)
LD = ld $(LDFLAGS)
OD = objdump $(ODFLAGS)
LD2 = ../../tools/ld2/ld2
WF = ../../tools/wf/wf
IMAGE = ../../sgos2.img

OBJECTS = $(patsubst %.cpp,%.o,  $(wildcard *.cpp)) \
	$(patsubst %.c,%.o,  $(wildcard *.c))

all: $(PROGRAM).exe

$(PROGRAM).exe: $(OBJECTS)
	$(LD) $(OBJECTS) -o$(PROGRAM).exe
	$(OD) $(PROGRAM).exe > $(PROGRAM).dmp
	$(WF) $(IMAGE) -src $@ -dest sgos/$@

# Standard Procedures
.cpp.o:
	$(CXX) -c -o $@ $<
.c.o:
	$(CC) -c -o $@ $<

clean:
	$(RM) $(OBJECTS)
	$(RM) $(PROGRAM).dmp
	$(RM) $(PROGRAM).exe
