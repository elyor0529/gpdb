#-------------------------------------------------------------------------
# This directory is for simple regression test for one GPDB release, plus
# one-compile multi-backend test.  Set USE_PGXS=1 to build against
# installed GPDB with pg_config, otherwise it's built with source tree.
#
# Since we keep the source identical between different GPDB releases,
# this Makefile finds GP_VERSION_NUM and runs appropriate test cases only.
# We assume user libraries use PGXS, so this Makefile is a bit too verbose
# as a simple developer example.  Essentially, user libraries can follow
# normal PGXS convention except PG_CPPFLAGS and SHLIB_LINK should be set
# pointing to gppc headers and library.  Or, they can even use only pg_config
# without PGXS.
#-------------------------------------------------------------------------

MODULE_big = gppc_demo
OBJS = gppc_demo.o
REGRESS = gppc_demo

PG_CONFIG = pg_config
PGXS := $(shell $(PG_CONFIG) --pgxs)

PG_CPPFLAGS = -I$(shell $(PG_CONFIG) --includedir)
SHLIB_LINK = -L$(shell $(PG_CONFIG) --libdir) -lgppc
include $(PGXS)

REGRESS_OPTS = --dbname=gppc_demo --init-file=init_file

installcheck: install
