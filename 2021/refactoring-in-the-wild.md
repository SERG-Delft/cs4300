---
layout: tud
title: Refactoring in the wild, with Diomidis Spinellis and TBD
---

We have two talks:

* Diomidis Spinellis on _CScout, the C refactoring browser_: Despite its maturity and popularity, 
the C programming language still
lacks tool support for reliably performing even simple refactoring,
browsing, or analysis operations. This is primarily due to identifier
scope complications introduced by the C preprocessor. The CScout
refactoring browser analyses complete program families by tagging the
original identifiers with their precise location and classifying them
into equivalence classes orthogonal to the C language's namespace and
scope extents. A web-based user interface provides programmers with an
intuitive source code analysis and navigation front-end, while an
SQL-based backend allows more complex source code analysis and
manipulation. CScout has been successfully applied to many medium and
large open source and proprietary projects identifying thousands of
modest refactoring opportunities. Projects where CScout has been applied
include the Linux, FreeBSD, and Solaris kernels, Apache httpd, awk,
PostgreSQL, and gdb.

* TBD