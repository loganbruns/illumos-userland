#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#
include ../../make-rules/shared-macros.mk

COMPONENT_NAME=			getopt
COMPONENT_VERSION=		1.1.4
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=		sha256:41083d9993c26792851e79b81a0991996a3f61e14998fdd607615cc3bf933bab
COMPONENT_ARCHIVE_URL=		http://software.frodo.looijaard.name/$(COMPONENT_NAME)/files/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=		http://software.frodo.looijaard.name/getopt/

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/justmake.mk
include $(WS_TOP)/make-rules/ips.mk

COMPONENT_BUILD_ARGS+= CC="$(CC)"
COMPONENT_BUILD_ARGS+= CFLAGS="$(CFLAGS)"

$(BUILD_64): COMPONENT_BUILD_ARGS+= LDFLAGS+="-m64"

build:		$(BUILD_32_and_64)

COMPONENT_INSTALL_ARGS += prefix=/usr/gnu mandir=/usr/gnu/share/man

$(INSTALL_64): COMPONENT_INSTALL_ARGS += bindir=/usr/gnu/bin/$(MACH64)

install:	$(INSTALL_32_and_64)

test:		$(NO_TESTS)

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
