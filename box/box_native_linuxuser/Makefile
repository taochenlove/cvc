###################################################################
#automatic detection SDK and LOCALDIR
CUR_DIR := $(dir $(realpath $(firstword $(MAKEFILE_LIST))))
TRYSDK := $(shell if [ -n "$$SDK" ] ; then\
        echo $$SDK;\
        else\
        cd $(CUR_DIR); while /usr/bin/test ! -e RELEASE ; do \
        dir=`cd ../;pwd`;                       \
        if [ "$$dir" = "/" ] ; then             \
           echo Cannot find SDK in $(firstword $(MAKEFILE_LIST)) 1>&2; \
           exit 1;                              \
        fi ;                                    \
        cd $$dir;                               \
        done ;                                  \
        pwd;                                    \
        fi)
SDK ?= $(realpath ${TRYSDK})

ifeq ($(SDK),)
$(error Please run this in a tree)
endif
LOCALDIR = $(patsubst %/,%,$(subst $(realpath $(SDK))/,,$(CUR_DIR)))
####################################################################

CMD = V=0
CMD += J=4
# trying the latter
build:
	$(MAKE) $(CMD) OVRT=native.linuxuser -C $(SDK)/sal
	$(MAKE) $(CMD) OVRT=native.linuxuser -C $(SDK)/source
	$(MAKE) $(CMD) OVRT=native.linuxuser -C $(SDK)/os_model/linux/linux_um
	-$(MAKE) $(CMD) OVRT=native.linuxuser -C $(SDK)/tools/debug_tool/cli
	-$(MAKE) $(CMD) OVRT=native.linuxuser -C $(SDK)/test




