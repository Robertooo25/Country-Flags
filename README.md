# Country flags

This repository contains illustrations of country flags in SVG format, all the flags have the same outline geometry format, which makes this repository ideal for profile customization and interchangeable icons.

View the country flags available here: https://hampusborgos.github.io/country-flags/

## Flags are organized by name and format

The flags are named by their 2-letter ISO-3166 country code, except for the
constituent countries of Great Britain which have 6-letter codes "GB-ENG" etc).

Kosovo uses the user-assigned country code `XK`, which is not part of the ISO standard, but in use by several multinational organizations.

Also included is a JSON file that maps the ISO country code to the name of the
country.


## Get the flags

You can [download this repository](https://github.com/hampusborgos/country-flags/archive/refs/heads/main.zip). Or you can clone it. You can also [view all the flags here](https://hampusborgos.github.io/country-flags/).

You can also install this as a NPM module:

    npm install --save svg-country-flags


## Exporting to pngs

In addition to the the SVG "sources" for all flags, we've also provided PNG exports of the SVG renderings in 100px, 250px, and 1000px widths. If you're still using PNGs (SVGs are scalable, after all), and the pre-rendered versions don't fit your needs, use the following methods to get different widths:

### Arbitrary Width

You can run the node script 'build-pngs', you must first install the modules `svgexport` and `imagemin-cli`:

    npm install -g svgexport imagemin-cli
    npm run build-pngs -- 1000:

Replace `1000:` with whatever width you want (note the `:`), or type `:200` to get
PNGs with a height of 200px.

### Arbitrary Width Manually

If you cannot run the node script above, you can do the same steps manually.

Use a combination of `svgexport` and `imagemin-cli` from NPM to get that.
`imagemin` is very important because `svgexport` produces uncompressed PNGs which are several MB each.

Run the following commands in the `svg/` directory to get PNGs of a desired width:

    for file in *.svg; do svgexport $file "`basename $file svg`png" pad 1000: ; done
    imagemin *.png --out-dir=../compressed-pngs/
    rm *.png

The resultant files will be in the `compressed-pngs` folder. As before, `1000:` is the dimensions to export.
