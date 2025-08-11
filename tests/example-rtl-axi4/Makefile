#
# Copyright (c) 2018 Xilinx Inc.
# Written by Francisco Iglesias,
#            Edgar E. Iglesias.
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

-include ../../.config.mk

# VCS setup
VCS ?= vcs2018-mx
VCS_FLAGS ?= -full64 -sverilog -sysc

# SystemC locations
SYSTEMC ?= /usr/local/systemc-2.3.2/
SYSTEMC_INCLUDE ?= $(SYSTEMC)/include
SYSTEMC_LIBDIR ?= $(SYSTEMC)/lib-linux64

# Compiler and linker flags
CPPFLAGS += -I$(SYSTEMC_INCLUDE) -I ../../ -I ../ -I .
LDFLAGS += -L$(SYSTEMC_LIBDIR) -Wl,-rpath,$(SYSTEMC_LIBDIR)
LDLIBS += -lsystemc -pthread

SRC_V += axifull_dev.v axifull_dev_S00_AXI.v
SRC_CPP += example-rtl-axi4.cc

TARGETS += simv

################################################################################

all: $(TARGETS)

simv: $(SRC_V) $(SRC_CPP)
	$(VCS) $(VCS_FLAGS) -CFLAGS "$(CPPFLAGS)" -LDFLAGS "$(LDFLAGS)" $(SRC_V) $(SRC_CPP) -o $@ $(LDLIBS)

clean:
	$(RM) -r csrc simv.daidir ucli.key $(TARGETS)
