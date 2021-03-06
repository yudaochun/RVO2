# -*- mode: python -*-
# vi: set ft=python :

#
# BUILD
# RVO2 Library
#
# Copyright 2008 University of North Carolina at Chapel Hill
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Please send all bug reports to <geom@cs.unc.edu>.
#
# The authors may be contacted via:
#
# Jur van den Berg, Stephen J. Guy, Jamie Snape, Ming C. Lin, Dinesh Manocha
# Dept. of Computer Science
# 201 S. Columbia St.
# Frederick P. Brooks, Jr. Computer Science Bldg.
# Chapel Hill, N.C. 27599-3175
# United States of America
#
# <https://gamma.cs.unc.edu/RVO2/>
#

load("@rules_pkg//:pkg.bzl", "pkg_deb", "pkg_tar")

licenses(["notice"])

exports_files(
    ["LICENSE"],
    visibility = ["//visibility:public"],
)

pkg_tar(
    name = "doc",
    srcs = ["LICENSE"],
    mode = "0644",
    package_dir = "/usr/share/doc/RVO",
    visibility = ["//visibility:private"],
)

genrule(
    name = "pc",
    outs = ["RVO.pc"],
    cmd = """
cat << 'EOF' > $@
#
# RVO.pc
# RVO2 Library
#
# Copyright 2008 University of North Carolina at Chapel Hill
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Please send all bug reports to <geom@cs.unc.edu>.
#
# The authors may be contacted via:
#
# Jur van den Berg, Stephen J. Guy, Jamie Snape, Ming C. Lin, Dinesh Manocha
# Dept. of Computer Science
# 201 S. Columbia St.
# Frederick P. Brooks, Jr. Computer Science Bldg.
# Chapel Hill, N.C. 27599-3175
# United States of America
#
# <https://gamma.cs.unc.edu/RVO2/>
#

prefix=/usr
exec_prefix=$${prefix}
libdir=$${exec_prefix}/lib
includedir=$${prefix}/include/RVO

Name: RVO2 Library
Description: Optimal Reciprocal Collision Avoidance
URL: https://gamma.cs.unc.edu/RVO2/
Version: 2.0.3
Libs: -L$${libdir} -lRVO
Cflags: -I$${includedir}
EOF
""",
    visibility = ["//visibility:private"],
)

pkg_tar(
    name = "pkgconfig",
    srcs = ["RVO.pc"],
    mode = "0644",
    package_dir = "/usr/lib/pkgconfig",
    visibility = ["//visibility:private"],
)

pkg_tar(
    name = "RVO",
    extension = "tar.gz",
    visibility = ["//visibility:public"],
    deps = [
        ":doc",
        ":pkgconfig",
        "//src:include",
        "//src:lib",
    ],
)

pkg_deb(
    name = "deb",
    architecture = "amd64",
    data = ":RVO",
    depends = [
        "libc6",
        "libgcc1",
        "libstdc++6",
    ],
    description = "Optimal Reciprocal Collision Avoidance",
    homepage = "https://gamma.cs.unc.edu/RVO2/",
    maintainer = "Jamie Snape",
    package = "rvo",
    version = "2.0.3",
    visibility = ["//visibility:public"],
)
