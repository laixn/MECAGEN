# mar. janv.  7 15:25:19 CET 2014*
# MecaGen Team

# Output options:
NAME     = libisf
VERSION  = 1
MINOR    = 0
RELEASE  = 0
SONAME   = $(NAME).so.$(VERSION)
#SOTARGET = lib/$(SONAME).$(MINOR).$(RELEASE)
ARTARGET = lib/$(NAME).a

# Compiler:
CC      = g++
CFLAGS  = -O3 -Wall -fpic

# SDL:
ISDL     = $(shell sdl2-config --cflags)
#LSDL     = $(shell sdl2-config --libs)

# Files:
INC = ./includes
SRC = ./src

# Static library:
AR      = ar cr

# Dynamic library:
#SO      = gcc -shared -Wl,-soname,$(SONAME)

########################################################################################################################
# Headers dependences:
HEADERS = $(wildcard $(INC)/*.hpp)
# Object to build:
OBJECTS = $(patsubst %.cpp, %.o, $(wildcard $(SRC)/*.cpp))
########################################################################################################################

.PHONY: all clean cleanall
.PRECIOUS: $(SOTARGET) $(ARTARGET) $(OBJECTS)

#all: $(SOTARGET) $(ARTARGET)
all: $(ARTARGET)

$(OBJECTS): %.o: %.cpp $(HEADERS)
	$(CC) $(CFLAGS) -I$(INC) $(ISDL) -c $< -o $@

$(ARTARGET): $(OBJECTS)
	mkdir -p lib
	$(AR) $@ $(OBJECTS)

#$(SOTARGET): $(OBJECTS)
#	$(SO) -o $@ $(OBJECTS) $(LSDL)

########################################################################################################################

clean:
	rm -f $(OBJECTS)

cleanall: clean
	rm -f $(ARTARGET)
#	rm -f $(ARTARGET) $(SOTARGET)
