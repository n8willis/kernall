Kerning and letterspacing research
===========================================

This repository hosts material that I am collecting about various
approaches to the automation of letterspacing and kerning.

Note that by "collecting," present tense, I subtly indicate that
the contents of the repository are not likely, at any arbitrary point
in time, to be in a state which one should regard as "complete."
Therefore if you notice something I have left out or otherwise missed,
please do feel free to drop an angry pull request that adds it or to
express your outrage at my shortsightedness through different means.

Spacing
-------

Classical heuristics have been described by a number of authors,
including Walter Tracy and Adrian Frutiger.

The [Tracy method](tracy.md) defines a small set of spacing values&mdash;in
a fixed ratio to each other&mdash;to be assigned as the left and right
sidebearings for most of the Latin uppercase and lowercase letters.
The base value from which the other spacing values are derived is
taken from the distance between the stems of n and H, so in a small
sense it can be said to "automate" spacing decisions.

However, Tracy's approach leaves out several glyphs, which he says
"must be spaced visually," and it is limited solely to the basic Latin
alphabet, as well as assuming an upright Roman form with serifs and
traditonal dimensions.

[Adrian Frutiger](frutiger.md) was said to use a similar systematic
approach to spacing, although he made only a few comments about his method.

Tracy's approach was [used](zapf.md) by Hermann Zapf to develop the automatic
spacing functionality later found in several Adobe applications.

The [wedge method](kindersley.md) developed by David Kindersley sought to find the
"optical center" of each glyph&mdash;that is, horizontal point at which a
vertical line drawn through the glyph produces an equal "gray ratio"
(that is, percentage of black) on each side.  

[LetterModel](lettermodel.md) is an approach to
letterspacing developed by Frank E. Blokland, and based on the notion
that early miniscules were drawn on a (relatively large-scale, with
respect to letter size) regular grid system.

AutoSpace by Andres Torresi of Huerta Tipográfica is an add-on for the
Glyphs font editor.  It has been demonstrated in several widely
shared online videos, but has not yet been formally released.

Pablo Impallari's [Spacing Macro](impallari.md) is a macro for FontLab.  It was initially inspired by Frank E. Blokland's LetterModel.

[Kernagic](kernagic.md) by Øyvind Kolås is a
standalone software tool that can automatically letterspace a UFO
font.  It implements several different letterspacing approaches

Kerning
-------

[Typefacet
Autokern](typefacet.md)
is a Python program by Charles M. Chen that can automatically adjust
side-bearings 
of kerning pairs in a font based on a set of user-supplied general arguments.

[BubbleKern](https://github.com/Tosche/BubbleKern) is an add-on for the
Glyphs font editor.

[iKern](http://ikern.com/k1/) by Igino Marini is a software service;
Marini [describes](http://ikern.com/k1/ikern/the-ikern-theory/) the
theory behind his approach, but the specific algorithms at the heart
of the method employed have not been published.

[KernMaster](http://www.fontmaster.nl/) is a component of the
FontMaster application suite, published by Dutch Type Library.



Ancillary utilities
-------------------

[LightMeter](https://github.com/LettError/LightMeter) is a RoboFont
utility that calculates the "grayness" percentage of a glyph or any
subselection of a glyph.  That is, it computes the ratio of black to
total area for the region of interest.

[FittingRoom](https://github.com/skosch/fittingroom) is a
letter-fitting utility that works by analyzing a set of glyphs and
breaking the set into classes, where each class has a similar enough
shape that it can be spaced using the same means.
