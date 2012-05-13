#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=			xmlstarlet
COMPONENT_VERSION=		1.3.1
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:effe9aba3f8003d1da2b07aa54af4f3b5956bd09f061c499442415278425885b
COMPONENT_ARCHIVE_URL=	http://downloads.sourceforge.net/project/xmlstar/xmlstarlet/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

CONFIGURE_OPTIONS+= CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS+= CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS+= --with-libxml-include-prefix=/usr/include/libxml2
CONFIGURE_OPTIONS+= --program-transform-name=s/xml/xmlstarlet/

# Fix man page name
COMPONENT_POST_INSTALL_ACTION = \
  mv $(PROTOUSRSHAREMANDIR)/man1/xmlstarletstarlet.1 $(PROTOUSRSHAREMANDIR)/man1/xmlstarlet.1 

# common targets
#
build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

test:		$(TESTS_32_and_64)

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
