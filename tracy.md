The Walter Tracy method of spacing letters
==========================================

In his book 'Letters of Credit', Walter Tracy defines a basic system
for spacing Latin lowercase and uppercase letters.  Each case begins
with a control character and defines a small set of spacing values
from it, which are then assigned to the left- and right-side bearings
of other letters.

For the lowercase letters, the control character is n.  The space
between the stems in n, divided by 2, is the starting point.  The
spacing should be adjusted optically, looking at a row full of "n"s.

Next, one should space the "o" by inserting it into a sequence of "n"s
and adjusting until the row looks equally balanced.  The "n" and "o"
are symmetrical with respect to the left and right sidebearings, and
the bearings of the other glyphs are derived from from these
measurements, based on whether or not the outer edge of the glyph is
straight or round.

Tracy notes that the sidebearings on "n" should be the maximum
sidebearings seen on any other letter in the typeface.  The derived
sidebearings he recommends are not precise; for the lowercase there
are six values:
- left sidebearing of n
- right sidebearing of n
- slightly more than left sidebearing of n
- minimum space
- same sidebearing as o
- slightly less than o

Tracy also says that a, f, g, s, t, and z must be spaced visually.

The same approach is repeated for the uppercase, starting with the
control character H.  Again, half of the inside counter is the
starting point, with the designer should adjust based on a sequences
of "H"s.  Similarly, "O" is the "round" standard, which is spaced
visually by inserting it among "H"s.

There are five derived sidebearings for the uppercase:
- same sidebearing as H
- slightly less than sidebearing of H
- about half of the sidebearing of H
- minimum space
- same sidebearing as O

For the uppercase, Tracy only notes S as needing visual spacing.  He
also notes that the sidebearings of H should be the maximum used for
any uppercase letter.

These values are listed in the table below:


| lb |glyph| rb |   | lb |glyph| rb |
|----|-----|----|---|----|-----|----|
| mn |  A  | mn |   |    |  a  |    |
| H  |  B  | ½H |   | nl |  b  | o  |
| O  |  C  | ½H |   | o  |  c  | o- |
| H  |  D  | O  |   | o  |  d  | nl |
| H  |  E  | ½H |   | o  |  e  | o- |
| H  |  F  | ½H |   |    |  f  |    |
| O  |  G  | H- |   |    |  g  |    |
| H  |  H  | H  |   | +n |  h  | nr |
| H  |  I  | H  |   | +n |  i  | nl |
| mn |  J  | H  |   | nl |  j  | nl |
| H  |  K  | mn |   | +n |  k  | mn |
| H  |  L  | mn |   | +n |  l  | nl |
| H- |  M  | H  |   | nl |  m  | nr |
| H- |  N  | H- |   | nl |  n  | nr |
| O  |  O  | O  |   | o  |  o  | o  |
| H  |  P  | O  |   | +n |  p  | o  |
| O  |  Q  | O  |   | o  |  q  | nl |
| H  |  R  | mn |   | nl |  r  | mn |
|    |  S  |    |   |    |  s  |    |
| mn |  T  | mn |   |    |  t  |    |
| H  |  U  | H- |   | nr |  u  | nr |
| mn |  V  | mn |   | mn |  v  | mn |
| mn |  W  | mn |   | mn |  w  | mn |
| mn |  X  | mn |   | mn |  x  | mn |
| mn |  Y  | mn |   | mn |  y  | mn |
| ½H |  Z  | ½H |   |    |  z  |    |


Analysis
--------

Perhaps the most striking feature of Tracy's approach is its
conservatism; it does not attempt to deterministically derive all of
the sidebearings from a single control character.  The designer starts
by visually spacing two glyphs each in the upper- and lowercase, and
must visually space several others at the end.

There are more subtle differences with other spacing heuristics,
however.  Tracy's approach does not assign a "straight sided"
sidebearing to the right side of a or the left side of f or t, nor
does it assign a "rounded" sidebearing to g, s, or S.

Furthermore, it assigns asymmetric (or possibly asymmetric)
sidebearings to several glyphs that are often treated as having
symmetric sides: h, i, l, m, J, M, and U, for example, are all given
symmetric sidebearings in the [LetterModel](lettermodel.md) approach.

Speaking of asymmetries, it is also noteworthy that Tracy's approach
does _not_ assume that the left and right sidebearings of "n" are the
same.  "n" and "m" are spaced the same, so they are both either
symmetric or asymmetric.

However, depending on the spacing of "n",
the "slightly more than left sidebearing of n" value may or may not
also euqal the /right/ sidebearing of n.  If it does, then "h" is
symmetric while "n" and "m" are not.

The approach does, however, assume that o, H, and O are all spaced
symmetrically.

Limitations
-----------

From an automation standpoint, Tracy's method is only a partial
solution (which is not to suggest, of course, that he every claimed
otherwise).  Within its prescribed use cases, though, it also makes
some broad assumptions about general, upright Roman forms.  However,
since so much of it relies on the designer's visual
spacing&mdash;particularly on the usual "outlier" glyphs&mdash;it may
be applicable to a wide range of styles.
