vtf2png
datetime: 2019-03-28 16:31:09

`vtf2png` is a command line tool to extract images from the VTF format used by
Valve's Source Engine. It supports a variety of pixel data formats, including
most of the RGBA variations and DXT compression formats.

The only dependencies are libpng and argp.

Compile on Linux:

Compile on Mac:
```
# libpngはもともと入ってたから調べてない
brew install argp-standalone
clang -lpng -largp vtf2png.c
```

**Usage:**

一括更新
```
for i in materials/vgui/**/*.vtf; do o=`echo $i | sed s/vtf$/png/` && ./a.out $i $o && echo $o; done
find materials/vgui/ -name '*.png' | xargs -J% cp -p % public/campaigns/xxx/
```

Export an image: `./vtf2png some.vtf out.png`

Export a specific frame: `./vtf2png -f 17 some.vtf out.png`
