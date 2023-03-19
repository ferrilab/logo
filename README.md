# Ferrilab Logo

The logo is hand-written SVG. Some parts of it may be useful for other Rust
projects.

## Components

The `base.svg` file is a 104px-square image containing an empty chainring and
some predefined utilities for building your own logo. The interior space of the
chainring is a circle with an 80px radius to the edge of the chainring and a
72px radius to the tip of the inner mounting sprockets. The annulus from 72px to
80px is open for use, but the marked area for inserting your logo will be
overdrawn by the mounting sprockets.

You can select either five sprockets (matching the Rust logo) or six (arranged
in a wide regular hexagon: sprockets at the equator and at 60deg latitude each
direction) by removing or adding the `sprockets-6` class to the `#logo-square`
element.

The utility classes `.{fg,bg,accent}-{trace,solid}` provide three colors of
outer stroke and inner fill, respectively. The `fg` color is near-black, the
`bg` color is near-white, and the default `accent` color is Rust Foundation
Orange. Three other oranges are also provided, sampled from the Ferris logos on
<https://rustacean.net>.

## Why Doesn’t It Look Exactly Like The Rust Logo?

The only available asset for the Rust logo is a machine-written SVG file that
is only broken into two components, and unfortunately they are *not* the
chainring and the Big R, so I had to build this from scratch. I elected to make
the spokes look slightly more like the bicycle chainring images I found by
searching for the term (scooped instead of triangular edges), and use 24 instead
of 32 to make them slightly more visually apparent at small sizes.

## How Can I Use It?

The SVG co-ordinate space runs from `-104 -104` in the top left to `104 104` in
the bottom right. `0 0` is at the exact center of the image, and there is a
commented-out `<circle r="1" />` element left in the file that you can enable to
get a visual reference.

Insert your logo code at the comment “Your logo goes here”, inside `#logo-main`.
You can draw anywhere within the view-box, but the chainring will overdraw you
and serve as a clip mask. The chainring is composed of both `.fg-` and `.bg-`
elements in order to ensure that your logo does not appear in the mounting holes
or between the teeth. This also gives the chainring visibility when displayed
against a dark background.

The interior of the chainring is filled with a `<circle .bg-solid />` element.
You can remove this if you prefer a transparent base, but remember that the
chainring affirmatively uses negative space, and that you can then only use
colors that contrast against both black and white backgrounds.

If you wish to embed your logo in a web page, remember: only web-safe fonts can
be portably used in an SVG. While you can use CSS `@import` rules to bring
external fonts into the SVG’s own stylesheet, these fonts are *not* loaded when
the browser renders an `<img src="your-logo.svg" />` element. If you use your
own font, you have to either embed the SVG text directly into the page, or
pre-render your logo as a raster image.

## Exporting to PNG and ICO

The best SVG rendering software generally available, and the software that will
most often be rendering your logo, is a web browser. Therefore, the best way to
convert your logo to a raster image is to view the file in your browser, and use
the Page Inspector tool’s “Screenshot Node” command. Don’t forget to set the
`<svg width="maxwidth" height="maxheight">` attributes first, so that your
screenshot has the requested dimensions rather than filling the entire viewport!
You can take multiple screenshots with different dimensions to be sure that you
are happy with the image at each size.

You can then use ImageMagick to strip the white corners and to combine several
images into a `.ico` bundle.

1. `convert ss-orig.png -transparent white ss2.png` strips the white corners
   from the image
1. `convert ss-*.png favicon.ico` bundles all the screenshots it can find into a
   favicon.

If you want to render and resize on the command-line instead of the browser, you
can use [this StackOverflow answer][0]. I haven’t tried it with this SVG file
and don’t care to.

## Licensing

This README and `base.svg` are CC0. `ferrilab.svg` is CC BY-NC-ND. Use of the
Ferrilab logo is permitted with the requirement that your copy-text clearly
indicates that you are referring *to* the Ferrilab project, and not representing
yourself *as part of* the Ferrilab project.

[0]: https://stackoverflow.com/questions/39256104/how-to-convert-an-image-file-from-svg-to-a-multi-size-ico-without-blur-sharp
