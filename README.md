# Ferrilab Logo

The logo is hand-written SVG, enclosed in [the Rust Project’s chainring art][0].

## Ferrilab

The Ferrilab project is composed of three crates:

- `funty`, which provides generalizations over the Rust primitives
- `radium`, which abstracts over different providers of shared mutability
- `bitvec`, which provides bit-precision addressing

It is actually a complete coïncidence that the project name, “Ferrilab”,
contains the first letter of each of these crates. It is also a coïncidince that
a potential fourth crate, `lilliputian`, uses the fourth consonant. But since an
abbreviation of the project name is also an acronym of the project components,
it felt very natural to use that as the text.

The orange glyph is a modified voltage-transformer symbol. I felt it was
appropriate, as all of these crates act like a semantic analogue to an
electrical transformer: in exchange for a reduction of raw available power and
capability, you gain increased flexibility and expressiveness.

The font is [“Ferro Rosso”][1].

## Components

The `base.svg` file is a copy of the Rust chainring, vendored here for
convenience. It is extended with some support items for rapidly beginning an
interior logo.

The utility classes `.{fg,bg,accent}-{trace,solid}` provide three colors of
outer stroke and inner fill, respectively. The `fg` color is near-black, the
`bg` color is near-white, and the default `accent` color is Rust Foundation
Orange. Three other oranges are also provided, sampled from the Ferris logos on
<https://rustacean.net>.

## How Can I Use It?

The SVG co-ordinate space runs from `-106 -106` in the top left to `106 106` in
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
can use [this StackOverflow answer][2]. I haven’t tried it with this SVG file
and don’t care to.

## Licensing

- `base.svg` is CC-BY. The visual artifact and the original SVG code that
  produces it are provided by the Rust Foundation. The SVG text provided here
  was modified by the Ferrilab Project.
- `README.md` is CC-BY, written by the Ferrilab Project.
- `ferrilab.svg` is CC BY-NC-ND. Use of the Ferrilab logo is permitted with the
  requirement that your copy-text clearly indicates that you are referring *to*
  the Ferrilab project, and not representing yourself *as part of* the Ferrilab project.

[0]: https://github.com/rust-lang/rust-artwork/blob/master/logo/rust-logo-gear-only.svg
[1]: https://www.1001fonts.com/ferro-rosso-font.html
[2]: https://stackoverflow.com/questions/39256104/how-to-convert-an-image-file-from-svg-to-a-multi-size-ico-without-blur-sharp
