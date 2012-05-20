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

COMPONENT_NAME=			xmlstarlet
COMPONENT_VERSION=		1.3.1
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=		sha256:effe9aba3f8003d1da2b07aa54af4f3b5956bd09f061c499442415278425885b
COMPONENT_ARCHIVE_URL=		http://downloads.sourceforge.net/project/xmlstar/xmlstarlet/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=		http://xmlstar.sourceforge.net

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

CONFIGURE_OPTIONS+= CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS+= CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS+= --with-libxml-include-prefix=/usr/include/libxml2
CONFIGURE_OPTIONS+= --program-transform-name=s/xml/xmlstarlet/

build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

# Fix man page name
COMPONENT_POST_INSTALL_ACTION = \
  mv $(PROTOUSRSHAREMANDIR)/man1/xmlstarletstarlet.1 $(PROTOUSRSHAREMANDIR)/man1/xmlstarlet.1 

COMPONENT_TEST_TARGETS =	check

test:		$(TEST_32_and_64)

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
