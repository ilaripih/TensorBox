SHELL := /bin/bash

.PHONY: all
all:
	pip3 install runcython3
	makecython3++ stitch_wrapper.pyx "" "stitch_rects.cpp ./hungarian/hungarian.cpp"

hungarian: hungarian/hungarian.so

hungarian/hungarian.so:
	cd hungarian && \
	TF_INC=$$(python3 -c 'import tensorflow as tf; print(tf.sysconfig.get_include())') && \
	g++ -std=c++11 -shared hungarian.cc -o hungarian.so -fPIC -I $$TF_INC -I $$TF_INC/external/nsync/public/ -O2;
