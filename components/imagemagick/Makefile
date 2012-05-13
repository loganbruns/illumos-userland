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

#
# Copyright (c) 2011, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=			ImageMagick
COMPONENT_MAJOR_VERSION=	6.7.5
COMPONENT_MINOR_VERSION=	10
COMPONENT_VERSION=		$(COMPONENT_MAJOR_VERSION)-$(COMPONENT_MINOR_VERSION)
COMPONENT_SRC=			$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=		$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:613146aefeeec31a8663b006664af9f9622d901c9698d9c0a49c6036467a0905
COMPONENT_ARCHIVE_URL=	ftp://ftp.imagemagick.org/pub/ImageMagick/legacy/$(COMPONENT_ARCHIVE)

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

# IPS_COMPONENT_VERSION is by default set to $(COMPONENT_VERSION) but in
# this case we need to replace the '-' by '.'.
#
IPS_COMPONENT_VERSION=	$(COMPONENT_MAJOR_VERSION).$(COMPONENT_MINOR_VERSION)
PKG_MACROS += COMPONENT_MAJOR_VERSION=$(COMPONENT_MAJOR_VERSION)

# The archive contains pre-generated magick-config.h header, which is later on
# being used and the build fails.  However, we want to use the header generated
# by configure from BUILD_DIR_32 / BUILD_DIR_64 directory, so the pre-generated
# header file needs to be deleted.
#
COMPONENT_PREP_ACTION= (cd $(@D) ; $(RM) magick/magick-config.h)

# To get the Perl modules built it is necessary to copy the PerlMagick directory
# to the build directory
#
COMPONENT_PRE_CONFIGURE_ACTION= ($(CP) -R $(SOURCE_DIR)/PerlMagick $(@D))

# Show name of "error tag" as part of the warning
#
CFLAGS+= -errtags

CONFIGURE_OPTIONS+= CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS+= CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS+= --with-modules
CONFIGURE_OPTIONS+= --enable-shared=yes
CONFIGURE_OPTIONS+= --enable-static=no
CONFIGURE_OPTIONS+= --without-gvc
CONFIGURE_OPTIONS.32+= --with-perl=$(PERL)
CONFIGURE_OPTIONS.32+= --with-perl-options="INSTALLDIRS=vendor"
CONFIGURE_OPTIONS.64+= --without-perl

# common targets
#
build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

# ImageMagick tests have hard-coded absolute paths inside, so essentially they
# can be run only after ImageMagick is actually installed and this is not 
# possible, so the tests are not invoked.
#
test:		$(NO_TESTS)
	@echo "Tests can be run only after ImageMagick is installed."

BUILD_PKG_DEPENDENCIES= $(BUILD_TOOLS)

include ../../make-rules/depend.mk
