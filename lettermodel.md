Frank Blokland's LetterModel method of spacing
==============================================

[LetterModel](http://www.lettermodel.org/) is spacing system described
by calligrapher and type designer Frank E. Blokland, resulting from
his doctoral research into historic type design and manufacturing.

Part of Blokland's central thesis is that Rennaissance punches were
cut in alignment with a "cadence" grid system; between any two particular
typefaces, the number of units in the grid might vary, but, within a
single face, stems, counters, extenders, and sidebearings were aligned
to grid coordinates.

At his research blog, Blokland [describes]
(http://www.lettermodel.org/wordpress/?p=316) how the grid-based
approach can be applied to typefaces designed without a grid in mind
(or, in practical terms, typefaces designed on the fine-scale
coordinate grids inherent in TrueType or PostScript curves).

First, a
grid should be superimposed on the "n" glyph, with the number of units
adjusted so that both stems are aligned on veritcal grid
lines.

Second, the sidebearings are set so that each bearing is half
the width of the counter inside the "n." From there, the sidebearings
for the other glyphs can be computed algebraically.

For his example,
Blokland applies a 36-unit grid over a normally-proportioned Roman
face, and provides a chart listing the left and right sidebearings
for the full uppercase and lowercase basic Latin alphabet, plus the
period and comma.

Below is the resulting "cadence" table.  Here, `x` indicates that the
bearing measurement is taken from the x-axis extremum, while `s`
indicates that the bearing is measured from the outer edge of the glyph's
stem:

| lb |glyph| rb |   | lb |glyph| rb |
|----|-----|----|---|----|-----|----|
| 1x |  A  | 1x |   | 2x |  a  | 6s |
| 8s |  B  | 3x |   | 5s |  b  | 2x |
| 3x |  C  | 2x |   | 2x |  c  | 1x |
| 8s |  D  | 3x |   | 2x |  d  | 6s |
| 8s |  E  | 2x |   | 2x |  e  | 1x |
| 8s |  F  | 2x |   | 6s |  f  | 1x |
| 3x |  G  | 6s |   | 2x |  g  | 1x |
| 8s |  H  | 8s |   | 6s |  h  | 6s |
| 8s |  I  | 8s |   | 6s |  i  | 6s |
| 6s |  J  | 6s |   | 6s |  j  | 5s |
| 8s |  K  | 1x |   | 6s |  k  | 1x |
| 8s |  L  | 2x |   | 6s |  l  | 6s |
| 8s |  M  | 8s |   | 6s |  m  | 6s |
| 8s |  N  | 8s |   | 6s |  n  | 6s |
| 3x |  O  | 3x |   | 2x |  o  | 2x |
| 8s |  P  | 2x |   | 6s |  p  | 2x |
| 3x |  Q  | 3x |   | 2x |  q  | 5s |
| 8s |  R  | 1x |   | 6s |  r  | 1x |
| 3x |  S  | 3x |   | 3x |  s  | 3x |
| 1x |  T  | 1x |   | 5x |  t  | 1x |
| 6s |  U  | 6s |   | 5s |  u  | 5s |
| 1x |  V  | 1x |   | 1x |  v  | 1x |
| 1x |  W  | 1x |   | 1x |  w  | 1x |
| 1x |  X  | 1x |   | 1x |  x  | 1x |
| 1x |  Y  | 1x |   | 1x |  y  | 1x |
| 2x |  Z  | 2x |   | 2x |  z  | 2x |
| 3x |  .  | 3x |   | 3x |  ,  | 3x |

The original table contains an oddity for "d", saying "left and right
from x-axis extreme, right from stem."  Presumably the conflicting
statements about the right sidebearing are a mere
clerical error; the intent is surely to measure from the stem.

The footer to the table also notes "the only area which counts, is
within the x-height / the capital spaces are lc + 1."  The surrounding
text does not go into detail on this point; the simplest explanation
is that one should increment each sidebearing on the capitals by one
grid unit:

| lb |glyph| rb |   | lb |glyph| rb |
|----|-----|----|---|----|-----|----|
| 2x |  A  | 2x |   | 2x |  a  | 6s |
| 9s |  B  | 4x |   | 5s |  b  | 2x |
| 4x |  C  | 3x |   | 2x |  c  | 1x |
| 9s |  D  | 4x |   | 2x |  d  | 6s |
| 9s |  E  | 3x |   | 2x |  e  | 1x |
| 9s |  F  | 3x |   | 6s |  f  | 1x |
| 4x |  G  | 7s |   | 2x |  g  | 1x |
| 9s |  H  | 9s |   | 6s |  h  | 6s |
| 9s |  I  | 9s |   | 6s |  i  | 6s |
| 7s |  J  | 7s |   | 6s |  j  | 5s |
| 9s |  K  | 2x |   | 6s |  k  | 1x |
| 9s |  L  | 3x |   | 6s |  l  | 6s |
| 9s |  M  | 9s |   | 6s |  m  | 6s |
| 9s |  N  | 9s |   | 6s |  n  | 6s |
| 4x |  O  | 4x |   | 2x |  o  | 2x |
| 9s |  P  | 3x |   | 6s |  p  | 2x |
| 4x |  Q  | 4x |   | 2x |  q  | 5s |
| 9s |  R  | 2x |   | 6s |  r  | 1x |
| 4x |  S  | 4x |   | 3x |  s  | 3x |
| 2x |  T  | 2x |   | 5x |  t  | 1x |
| 7s |  U  | 7s |   | 5s |  u  | 5s |
| 2x |  V  | 2x |   | 1x |  v  | 1x |
| 2x |  W  | 2x |   | 1x |  w  | 1x |
| 2x |  X  | 2x |   | 1x |  x  | 1x |
| 2x |  Y  | 2x |   | 1x |  y  | 1x |
| 3x |  Z  | 3x |   | 2x |  z  | 2x |
| 3x |  .  | 3x |   | 3x |  ,  | 3x |

Normalization
-------------

The example discussed on the linked page resulted in left and right sidebearings
of 6 for the "n." Naturally, the relative proportions of all the
remaining bearings can be computed from that.  Doing so would produce
the following relative (to "n") set of bearings:

| lb |glyph| rb |   | lb |glyph| rb |
|----|-----|----|---|----|-----|----|
| 0.333x |  A  | 0.333x |   | 0.333x |  a  | 1.0s |
| 1.500s |  B  | 0.667x |   | 0.833s |  b  | 0.333x |
| 0.667x |  C  | 0.5x |   | 0.333x |  c  | 0.167x |
| 1.500s |  D  | 0.667x |   | 0.333x |  d  | 1.0s |
| 1.500s |  E  | 0.5x |   | 0.333x |  e  | 0.167x |
| 1.500s |  F  | 0.5x |   | 1.0s |  f  | 0.167x |
| 0.667x |  G  | 1.167s |   | 0.333x |  g  | 0.167x |
| 1.500s |  H  | 1.500s |   | 1.0s |  h  | 1.0s |
| 1.500s |  I  | 1.500s |   | 1.0s |  i  | 1.0s |
| 1.167s |  J  | 1.167s |   | 1.0s |  j  | 0.833s |
| 1.500s |  K  | 0.333x |   | 1.0s |  k  | 0.167x |
| 1.500s |  L  | 0.5x |   | 1.0s |  l  | 1.0s |
| 1.500s |  M  | 1.500s |   | 1.0s |  m  | 1.0s |
| 1.500s |  N  | 1.500s |   | 1.0s |  n  | 1.0s |
| 0.667x |  O  | 0.667x |   | 0.333x |  o  | 0.333x |
| 1.500s |  P  | 0.5x |   | 1.0s |  p  | 0.333x |
| 0.667x |  Q  | 0.667x |   | 0.333x |  q  | 0.833s |
| 1.500s |  R  | 0.333x |   | 1.0s |  r  | 0.167x |
| 0.667x |  S  | 0.667x |   | 0.5x |  s  | 0.5x |
| 0.333x |  T  | 0.333x |   | 0.833x |  t  | 0.167x |
| 1.167s |  U  | 1.167s |   | 0.833s |  u  | 0.833s |
| 0.333x |  V  | 0.333x |   | 0.167x |  v  | 0.167x |
| 0.333x |  W  | 0.333x |   | 0.167x |  w  | 0.167x |
| 0.333x |  X  | 0.333x |   | 0.167x |  x  | 0.167x |
| 0.333x |  Y  | 0.333x |   | 0.167x |  y  | 0.167x |
| 0.5x |  Z  | 0.5x |   | 0.333x |  z  | 0.333x |
| 0.5x |  .  | 0.5x |   | 0.5x |  ,  | 0.5x |

Consequently, it is not strictly
necessary to space the "n" first, if all of the glyphs conform to
LetterModel's underlying stylistic assumptions (e.g., Renaissance
forms).

Analysis
--------

From a practical standpoint, the LetterModel
cadence system is more complete than Tracy's method (which omitted
several letters), and it does not begin with an "optical fitting" step
for the starting glyph ("n" for the cadence method, as opposed to "n"
and "o" for the Tracy method).

Interestingly enough, the automatic
bearings chosen by the cadence method are derived from half the width
of the "n", which is identical to the sidebearings prescribed by
Frutiger's approach.  Thus, the cadence method essentially combines
Tracy and Frutiger's approaches into a single method. 

There are some unique properties of the method in comparison with
other systems.  For instance, the cadence tables produce their minimal
right sidebearings on A, K, R, T, W, X, and Y, but not on L.  It is
also interesting that the bearings of the capitals are incremented by
a fixed amount, rather than scaled.

Limitations
-----------

The main limitation
is the method makes assumptions about the proportions and shapes of
the glyphs&mdash;namely, that they adhere to typical Rennaissance
forms. 

This is noticeable in a few key spots:

* The right sidebearing for g is measured from the
extremum, rather than from the stem. This works for the two-story g,
but is inappropriate for the one-story g.
* The right sidebearing for G is measured from the stem.  This
assumes that G has a more-or-less straight spur.
* The bearings of the capitals are incremented by a fixed amount, which
suggests that assumptions are made about the relative stroke size and
widths of the capitals with respect to the lower-case glyphs.

Further afield, the LetterModel method, like Tracy and Frutiger,
applies only to upright Roman forms, not to italics.
