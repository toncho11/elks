# Makefile for bcc library - 8086 assembler routines
#
#########################################################################
# Relative path to base directory.

BASEDIR 	= ../../..

#########################################################################
# Define the variables required by the standard rules - see the standard
# rules file (below) for details of these variables.

USEBCC 		= Y

CLEANDEP	= 

CLEANME 	= 

DEPEND  	= 

DISTFILES	= 

NOINDENT	=

#########################################################################
# Include the standard rules.

include $(BASEDIR)/Makefile-rules

#########################################################################
# Objects to be compiled.
# unused: atomic.S

# Precompiled assembly

SRCS1 = \
	fmemory.S \
	peekpoke.S \
	string.S \
	printreg.S \
	divmod.S \
	# end of list

ifeq ($(CONFIG_ARCH_PC98), y)
SRCS1 += bios1B-pc98.S bios1F-pc98.S unreal.S loadall.S
else ifeq ($(CONFIG_ARCH_SOLO86), y)
SRCS1 += unreal.S loadall.S
else
SRCS1 += bios13-ibm.S bios15-ibm.S unreal.S loadall.S
endif

OBJS1 = $(SRCS1:.S=.o)

# Non-precompiled assembly

SRCS2 =

OBJS2 = $(SRCS2:.s=.o)

# C sources

SRCS3 = \
	bitops.c \
	# end of list

ifeq ($(CONFIG_ARCH_IBMPC), y)
SRCS3 += prectimer.c
endif

OBJS3 = $(SRCS3:.c=.o)

OBJS		= $(OBJS1) $(OBJS2) $(OBJS3)


#########################################################################
# Commands.

all:	lib86.a

lib86.a: $(OBJS)
	$(AR) rcs lib86.a $(OBJS)

$(TMPS1): $(SRCS1)
$(OBJS1): $(TMPS1)
$(OBJS2): $(SRCS2)
$(OBJS3): $(SRCS3)

bios15-ibm.o: a20-ibm.inc

bios1F-pc98.o: a20-pc98.inc

#########################################################################
# Standard commands.

distdir:
	cp -pf Makefile $(SRCS1) $(SRCS2) $(SRCS3) $(DISTDIR)/arch/i86/lib

#########################################################################
### Dependencies:
