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

COMPONENT_NAME=			zzuf
COMPONENT_VERSION=		0.13
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=		sha256:0842c548522028c3e0d9c9cf7d09f6320b661f33824bb6df19ca209851bdf627
COMPONENT_ARCHIVE_URL=		http://caca.zoy.org/files/zzuf/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=		http://caca.zoy.org/wiki/zzuf

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

CONFIGURE_OPTIONS += CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS += LDFLAGS="$(LDFLAGS) -lnsl -lsocket"
COMPONENT_PRE_CONFIGURE_ACTION= ($(CP) -R $(SOURCE_DIR)/test $(@D))

COMPONENT_BUILD_ARGS += -j`/usr/sbin/psrinfo | grep on-line | wc -l | tr -d ' '`

build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

COMPONENT_TEST_TARGETS =	check

test:		$(TEST_32_and_64)

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
