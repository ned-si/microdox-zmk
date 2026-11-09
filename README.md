# microdox-zmk

My ZMK config for the Boardsource Microdox (v1) on nice!nano controllers, with
an EC11 encoder added on the right half.

Layout follows the
[unified ZMK config template](https://github.com/zmkfirmware/unified-zmk-config-template),
pinned to ZMK v0.3:

```
build.yaml                  build targets (board + shield per half)
config/west.yml             ZMK version
config/microdox.keymap      keymap, both halves; includes the *.dtsi next to it
config/microdox.conf        Kconfig, both halves
config/microdox_*.overlay   right-hand encoder (declared on both halves)
```

The shield itself is upstream ZMK's `microdox`; this repository only adds the
encoder.

## Get the firmware

Every push builds both halves in GitHub Actions. Open the run under the
Actions tab and download the `firmware` artifact: it holds
`microdox_left-nice_nano-zmk.uf2` and `microdox_right-nice_nano-zmk.uf2`.

## Flash

For each half: plug it in over USB, double-tap the reset button, and copy that
half's `.uf2` onto the `NICENANO` drive that appears. The drive unmounts on its
own when flashing is done. Flash both halves after a keymap change; the left
half is the central and holds the keymap, but both must run the same version.
