kernall: Kerning and letterspacing research
-------------------------------------------

This repository hosts material that I am collecting about various
approaches to the automation of letterspacing and kerning.

Note that by "collecting," present tense, I subtly indicate that
the contents of the repository are not likely, at any arbitrary point
in time, to be in a state which one should regard as "complete."
Therefore if you notice something I have left out or otherwise missed,
please do feel free to drop an angry pull request that adds it or to
express your outrage at my shortsightedness through different means.

Spacing
=======

Classic heuristics have been described by a number of authors,
including [Walter Tracy and Adrian Frutiger]
(http://web.archive.org/web/20081008042010/http://www.linotype.com/793-12659/walterkaechs.html).
Tracy's approach was used by Hermann Zapf to develop the automatic
spacing functionality later found in several Adobe applications.

The Wedge Method, developed by David Kindersley, sought to find the
"optical center" of each glyph --- that is, the point on the
horizontal axis at which the two sides of the glyph produced an equal
amount of gray.  Kindersley determined that this method produced
acceptable results only if the gray measurements were taken with the
center of the glyph masked off; the opacity and degree to which the
center of a glyph should be masked off for optimal results was the
focus of the research.

[LetterModel](http://www.lettermodel.org/) is an approach to
letterspacing developed by Frank E. Blokland, and based on the notion
that early miniscules were drawn on a (relatively large-scale, with
respect to letter size) regular grid system.

AutoSpace by Andres Torresi of Huerta Tipográfica is an add-on for the
Glyphs font editor.  It has been demonstrated in several widely
shared online videoes, but has not yet been formally released.

[Spacing Macro](http://www.impallari.com/projects/overview/spacing-macro) by Pablo
Impallari is a macro for FontLab.  It is based on discussions
[http://typedrawers.com/discussion/52/spacing-macro] at the
TypeDrawers forum, and was initially inspired by Frank E. Blokland's LetterModel.

[Kernagic](https://github.com/hodefoting/kernagic) by Øyvind Kolås is a
standalone software tool that can automatically letterspace a UFO
font.  It implements several different letterspacing approaches:
* LetterModel by Frank E. Blokland
* Snap Gap, which snaps "rhythm points" of glyphs to a desired grid
* Interactivos Average, a simple approach expressed in
https://gitorious.org/libregraphicsmag/interactivosbook .

Note that the Average method was dropped from later Kernagic releases,
as it did not produce results as satisfactory as the other methods.
It is mentioned here for the sake of completeness.

Kerning
=======

[Typefacet
Autokern](http://charlesmchen.github.io/typefacet/topics/autokern/index.html)
is a Python program using Robofab.

[BubbleKern](https://github.com/Tosche/BubbleKern) is an add-on for the
Glyphs font editor.

[iKern](http://ikern.com/k1/) by Igino Marini is a software service;
the algorithms at the heart of the method employed have not been
disclosed.

[KernMaster](http://www.fontmaster.nl/) is a component of the
FontMaster application suite, published by Dutch Type Library.



Ancillary utilities
===================

[LightMeter](https://github.com/LettError/LightMeter) is a RoboFont
utility that calculates the "grayness" percentage of a glyph or any
subselection of a glyph.  That is, it computes the ratio of black to
total area for the region of interest.

[FittingRoom](https://github.com/skosch/fittingroom) is a
letter-fitting utility that works by analyzing a set of glyphs and
breaking the set into classes, where each class has a similar enough
shape that it can be spaced using the same means.
