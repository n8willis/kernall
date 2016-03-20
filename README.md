kernall: Kerning and letterspacing research
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
-------

[Typefacet
Autokern](http://charlesmchen.github.io/typefacet/topics/autokern/index.html)
is a Python program using Robofab.

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
