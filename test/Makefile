# This source code is governed by by the boost v1 licensing terms and conditions.
# Copyright 2016 Nicholas A. Smith (nickrmc83@gmail.com)

# To build the test application with a non-default c++ compiler set environment
# variable CXX. For example to build with clang++ on an Ubuntu machine try:
# make clean && CXX=clang++ make
CXXFLAGS=-Wall -std=c++11 -g -O0
TARGET=event_bus_test
VPATH=../include
.PHONY=clean valgrind test

all: $(TARGET)

$(TARGET) : event_bus_test.cpp event_bus.hpp
	$(CXX) $(CXXFLAGS) -I../include -o $@ $< -pthread

clean:
	rm -f $(TARGET)

test: $(TARGET)
	./$^

valgrind: $(TARGET)
	valgrind --tool=memcheck --leak-check=full --show-leak-kinds=all ./$^
