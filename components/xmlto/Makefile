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

COMPONENT_NAME=			xmlto
COMPONENT_VERSION=		0.0.25
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=		sha256:361cb70d5d0b4b753db00b67ed8bc1d53d0bc96c407d0310aefe854470b7e536
COMPONENT_ARCHIVE_URL=		https://fedorahosted.org/releases/x/m/$(COMPONENT_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=		https://fedorahosted.org/xmlto/

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

CONFIGURE_OPTIONS+= CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS+= CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS+= GETOPT="/usr/gnu/bin/getopt"

build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

COMPONENT_TEST_TARGETS =	check

test:		$(TEST_32_and_64)

PKGMOGRIFY_TRANSFORMS+= remove-docbook-man

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
