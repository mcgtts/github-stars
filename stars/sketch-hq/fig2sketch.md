---
project: fig2sketch
stars: 130
description: |-
    fig2sketch is a command line tool that converts `.fig` files into Sketch design documents (`.sketch`), which can then be opened with Sketch applications.
url: https://github.com/sketch-hq/fig2sketch
---

# .fig to Sketch converter

fig2sketch is a command line tool that converts .fig files into Sketch design documents (.sketch), which can then be opened with [Sketch](https://www.sketch.com/) applications.

> [!IMPORTANT]
> Sketch `2025.1` introduced Frames as a replacement to Artboards. This was a breaking change in the Sketch file format, and has also been implemented as a breaking change in `fig2sketch`. If you are using Sketch `101` or older, you need to use fig2sketch `0.3.6`.

## How it works

fig2sketch reads design data from a .fig file and converts it into data that Sketch apps can open. While the conversion is as accurate as possible, the types of data supported by .fig files and .sketch documents are not exactly the same. This means that some data need to be prepared in slightly different ways so that they’re displayed with the highest fidelity possible in Sketch apps.

### Using the source code

1. Run `python src/fig2sketch.py <path to .fig file> <path to store the .sketch file>`
2. Open the resulting .sketch document in Sketch

### Using a release binary

1. Run `fig2sketch <path to .fig file> <path to store the .sketch file>`
2. Open the resulting .sketch document in Sketch

### Using a release from PyPi

1. Install with `pip install "fig2sketch[fast]"`
2. Run `fig2sketch <path to .fig file> <path to store the .sketch file>`
3. Open the resulting .sketch document in Sketch

### Parameters

To check all available options run:
```
python src/fig2sketch --help
```

Some important options:

- Choose an override option with `--instance-override` so you can decide whether to detach an instance or to just ignore it in case the instance is not supported as sketch instance
- Pass `--force-convert-images` if the original document contains a corrupted image and you want to force it instead of having an error
- Pass `--salt 12345678` to ensure a consistent conversion order
- Pass `--dump-fig-json example/fig_file.json` (whichever path/name you like) to dump the generated JSON from the .fig file
- Pass `-v` or `-vv` to show more information about he conversion process

Example:
```
python src/fig2sketch.py --salt 12345678 example/shapes_party.fig output/output.sketch --dump-fig-json example/fig_file.json
````

## Install

Before moving forward, you need Python 3.10 or newer installed in your machine.

```
python -m venv .venv
. .venv/bin/activate
pip install .
```

### Performance

Performance improvements are available for data read from the .fig file and also for output data serialization into the .sketch document. If you want to enjoy those performance improvements you need to follow some steps.

Make sure, first, that you have [Rust](https://www.rust-lang.org/) and [Cargo](https://doc.rust-lang.org/cargo/) installed on your machine. After installing Rust and Cargo you need to install [maturin](https://www.maturin.rs/) as well:

```
pip install maturin
```

Now, you can proceed to install the performance improvements:

```
pip install ".[fast]"
sh scripts/install_patched_orjson.sh
```


## Running the tests

Before running the tests for the first time, you'll need to install the dev requirements (within the virtual environment):

```
pip install ".[dev]"
```

Then, you can run the tests just executing this in the project root:

```
pytest
```

## Current support

fig2ksetch supports the most frequently used data in a .fig file. Essentially, common .fig files will be converted to .sketch documents and displayed almost identically to the intended representation of the original .fig file.

During the conversion process, fig2sketch will ignore .fig file data that don’t have a reasonable match in Sketch — but it will try to show a warning instead.

### Frames vs Artboards

Frames in .fig files are a way to group the layers that the files contain. Sketch documents have a similar concept called Artboards. However, while Frames can be nested and supposedly behave in the same way at every nesting or main level, Artboards in Sketch *only* exist at the main level inside the Canvas and can’t be nested.

Additionally, Frames and Artboards support different types of styling.

Because of these differences, fig2sketch usually applies two rules when transforming Frames:

- It will convert any Frame that’s nested inside another Frame to a Group, and it will add a background layer that contains the styles that the Frame originally had
- If the Frame is at the top level but contains styles that don’t match Sketch Artboard styles, it will convert the Frame to an Artboard and add a background layer containing the styles that the Frame originally had

This kind of transformation will happen with most .fig files, so it won’t show any warnings in the command output.

### Text rendering

Text rendering engines between platforms have multiple differences, and it's hard to always guarantee that texts look exactly the same between apps. You may find very sometimes very minor (almost unnoticeable differences).
Additionally, there are some other obvious differences between how Sketch and other tools opening .fig files display the data.
One clear difference, for example is about texts with fixed size. In sketch, if a text overflows the size of the layer, the overflowing text won't be visible. You may find that other apps that work with .fig do show the overflowing text when it takes more space than the fixed size of the box.

## About .sketch documents

.sketch documents are based on an open format, which you can [learn more](https://github.com/sketch-hq/sketch-document) about here, especially if you plan to contribute to the project.

## Want to contribute?

We would love for you to contribute to fig2sketch project! Pull requests are welcome. Take a look at the [contributing guidelines](CONTRIBUTING.md) for more details.

## License
The code and documentation in this project are released under the [MIT license](LICENSE)

