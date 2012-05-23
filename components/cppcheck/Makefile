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

COMPONENT_NAME=			cppcheck
COMPONENT_VERSION=		1.54
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=		sha256:d90236f863a6662ed6dffbadc8733a14def5f31d29d469893bc6e1fda741332f
COMPONENT_ARCHIVE_URL=		http://downloads.sourceforge.net/project/cppcheck/cppcheck/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=		http://cppcheck.sourceforge.net

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/justmake.mk
include $(WS_TOP)/make-rules/ips.mk

CXXFLAGS +=	-library=stlport4 -staticlib=stlport4
CXXFLAGS +=	$(studio_OPT)

COMPONENT_BUILD_ARGS += -j$(shell /usr/sbin/psrinfo | grep on-line | wc -l | tr -d ' ')
COMPONENT_BUILD_ARGS += all man
COMPONENT_BUILD_ARGS += HAVE_RULES=yes
COMPONENT_BUILD_ARGS += CXX="$(CXX)"
COMPONENT_BUILD_ARGS += CXXFLAGS="$(CXXFLAGS)"

build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

$(INSTALL_64): COMPONENT_INSTALL_ARGS += BIN=$(PROTOUSRBINDIR)/$(MACH64)

COMPONENT_POST_INSTALL_ACTION = \
  ($(MKDIR) $(PROTOUSRSHAREMANDIR)/man1 ; \
   $(CP) $(@D)/cppcheck.1 $(PROTOUSRSHAREMANDIR)/man1)

COMPONENT_TEST_TARGETS =	check

test:		$(TEST_32_and_64)

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
