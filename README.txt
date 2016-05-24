Description of files and subdirectories
---------------------------------------

srfi-130.html contains HTML for the SRFI 130 specification.  It
was written by John Cowan.

srfi-130-test.scm is a black-box test program.  It can be used to
test all three implementations contained within this directory.
For instructions on how to do so, see comments at the beginning
of the file.  The test program was written by Will Clinger.

This site contains three different sample implementations of
SRFI 130 in the subdirectories srfi-130, srfi, and foof:

    srfi-130 is an R7RS implementation that imports only from
    (scheme base), (scheme char), and (scheme cxr).  It was
    written by John Cowan, and is basically a port of Olin
    Shivers's sample implementation for SRFI 13.  Cursors
    are the same as indexes.

    srfi is an R7RS implementation that imports (srfi 13) instead
    of duplicating a large fraction of its code.  Its only import
    dependencies are (scheme base), (scheme case-lambda), (srfi 1),
    and (srfi 13), and the only procedure imported from (srfi 1) is
    last-pair.  It was written by Will Clinger, and is basically
    the implementation used in Larceny v0.99.  Cursors are the same
    as indexes.

    foof is an R7RS implementation that imports only from
    (scheme base), (scheme char), (scheme cxr), and (scheme case-lambda).
    It was written by Alex Shinn, and was extracted from various
    files that are part of Chibi.  Although cursors are the same
    as indexes, most of the code should still work if cursors were
    represented differently from indexes; that has not been tested.


Notes on porting
----------------

All three subdirectories contain a 130.sld file that uses R7RS
define-library to define the (srfi 130) library.  Translating
to %3a130.sls files for an R6RS library named (srfi :130) should
be straightforward.

The srfi-130 and foof subdirectories contain srfi-130.scm files
that are intended for use only in Chicken and would be used
instead of the 130.sld files in that implementation.

The other *.scm files that appear within the three subdirectories
contain R7RS code that is included by the 130.sld files.  It
should not be too hard to port those files to R5RS systems, but
some shims or changes may be needed for case-lambda and other
non-R5RS features.
