# Face image dataset duplicate information

This repository contains JSON files that list exact image file duplicates for the datasets

* [LFW](https://vis-www.cs.umass.edu/lfw/) (specifically the [lfw.tgz](http://vis-www.cs.umass.edu/lfw/lfw.tgz) with md5sum `a17d05bd522c52d84eca14327a23d494`), and
* the "Testing_Set/Gallery_Match" + "Testing_Set/Probe" subset of [TinyFace](https://qmul-tinyface.github.io/) (`tinyface.zip` with md5sum `d8f1b97e4fc1857ff6bc7cf49389aab6`).

Duplicates were detected using [BLAKE3 hashes via the "blake3" Python bindings](https://pypi.org/project/blake3/) at version 0.3.1.

The `*.blake3_duplicate_sets.json` files list the relative paths for the image files, sorted alphabetically, for equivalent BLAKE3 hashes:

```json
{
    "<one hexadecimal BLAKE3 hash value>": [
        "<relative image file path 1>",
        "<relative image file path 2>",
        "<... possibly further paths if more than two files correspond to the same hash ...>"
    ]
}
```

The `*.exclusion_list.json` files list the relative paths of duplicates, also sorted alphabetically, so that all these files could be excluded to only keep one image per hash value:


```json
[
    "<relative image file path>",
    "<relative image file path>",
    "<relative image file path>",
    "<...>"
]
```

I.e. an `*.exclusion_list.json` contains all paths except the first one per hash entry in the corresponding `*.blake3_duplicate_sets.json`.
