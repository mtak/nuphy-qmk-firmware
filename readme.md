# nuphy-qmk-firmware

Updated version of NuPhy's QMK firmware with my own changes:

* Increased debounce time (to avoid double key presses)
* Slightly changed key map:
  * Caps Lock changed to Ctrl
  * Caps Lock now is activated by pressing both shift keys at the same time ([Caps Word](https://docs.qmk.fm/features/caps_word))
  * Microphone mute button on F13
  * Some minor tweaks from the original, mostly to get back to normal TKL layout

To build:

1. Clone repo and [install QMK](https://docs.qmk.fm/newbs_getting_started)
1. Install submodules:

        git submodule update --force --recursive --init --remote

1. Fix header reference in `lib/chibios/os/rt/include/ch.h` r125:

        -#include "chlib.h"
        +#include "../oslib/include/chlib.h"

1. Set QMK home dir:

        qmk config user.qmk_home="/home/mtak/dev/nuphy-qmk-firmware"

1. Build:

        qmk compile -kb nuphy/gem80/ansi -km mtak

1. Flash (unplug keyboard, hold Esc, plug back in):

        qmk flash -kb nuphy/gem80/ansi -km mtak
