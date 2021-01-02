# Copyright 2020 Free Software Foundation, Inc.
#
# This file is part of GNU Radio
#
# SPDX-License-Identifier: GPL-3.0-or-later
#

GR_PYTHON_CHECK_MODULE_RAW(
    "pygccxml"
    "import pygccxml"
    PYGCCXML_FOUND
    )

include(GrPybind)

########################################################################
# Python Bindings
########################################################################

list(APPEND iqbalance_python_files
    fix_cc_python.cc
    optimize_c_python.cc python_bindings.cc)

GR_PYBIND_MAKE_OOT(iqbalance 
   ../..
   gr::iqbalance
   "${iqbalance_python_files}")

install(TARGETS iqbalance_python DESTINATION ${GR_PYTHON_DIR}/iqbalance COMPONENT pythonapi)
