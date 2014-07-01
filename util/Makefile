SWIG = swig
SWIG_OPTS = -c++ -python
CC = g++ 
OPTS = -fPIC -O3 -funroll-loops -msse3 -fopenmp 
PYTHON ?= python
PYTHON_INCLUDE_DIR = $(shell $(PYTHON) -c 'from distutils.sysconfig import get_python_inc; print(get_python_inc())')
PYTHON_CFLAGS = -I$(PYTHON_INCLUDE_DIR)

all: swig link

swig: semi_analyticalwrap.i
	$(SWIG) $(SWIG_OPTS) $?

link:  
	$(CC) $(OPTS) -c semi_analyticalwrap.cpp semi_analyticalwrap_wrap.cxx $(PYTHON_CFLAGS)
	$(CC) $(OPTS) -shared $? -o _semi_analyticalwrap.so semi_analyticalwrap.o semi_analyticalwrap_wrap.o

clean:
	rm -f _semi_analyticalwrap.so semi_analyticalwrap.o semi_analyticalwrap_wrap.o semi_analyticalwrap_wrap.cxx semi_analyticalwrap.py *.pyc

.cxx.o:
	$(CC) $(OPTS) -c $< -o $@

.cpp.o:
	$(CC) $(OPTS) -c $< -o $@
