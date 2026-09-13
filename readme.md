<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/klor-font-logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/klor-font-logo-bright.svg">
  <img alt="KLOR logo font" src="/docs/images/klor-font-logo-bright.svg">
</picture>

# ZMK CONFIG FOR THE KLOR SPLIT KEYBOARD

[Here](https://github.com/GEIGEIGEIST/qmk-config-klor) you can find the QMK config for the KLOR.\
[Here](https://github.com/GEIGEIGEIST/klor) you can find the hardware files and build guide.

KLOR is a 36-42 key column-staggered split keyboard. It supports a per key RGB matrix, encoders, OLED displays, a Pixart Paw3204 trackball and four different layouts, through brake off parts.

![KLOR layouts](/docs/images/klor-layouts.svg)

Polydactyl is the default layout. If you choose one of the other layouts you can use the matching template in the default keymap.


## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [github desktop](https://desktop.github.com/))
- adjust the klor.keymap file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the left half of the KLOR to your PC, press reset twice
- the keyboard should now appear as a mass storage device
- drag'n'drop the `klor_left-nice_nano_v2-zmk.uf2` file from the archive onto the storage device
- repeat this process with the right half and the `klor_right-nice_nano_v2-zmk.uf2` file.


## KNOWN ISSUES

- The encoder on the secondary side doesn't work yet. This is a limitation of ZMK.
- Need to add the code for the Pixart Paw3204 trackball.

## ZMK Studio

The firmware and GitHub build workflow are pinned to ZMK `v0.3`, which supports
Studio and this configuration's `nice_nano_v2` board names. Studio is enabled
only on the left (central) half, with USB communication and locking enabled.
The Studio view uses QMK's schematic Polydactyl layout: 42 keys plus two encoder
push-button positions, in the same order as the existing keymap.

After building successfully, flash the matching firmware to both halves. Connect
the left half using a USB data cable, then open https://zmk.studio/ in Chrome or
Edge, or use the native ZMK Studio app.

To unlock with only the left half powered, press the three top-row **Q + W + E**
positions together (the three outermost keys of the left top row, within 100 ms).
This combo works on every layer and remains at those physical positions if you
remap the letters in Studio. Rebuild and flash the updated left firmware first.

The base layer uses QWERTY, with hold-for-Shift on F and J. The existing Q + W
Escape combo is retained; both overlapping combos use a 100 ms window.

The original two-half unlock method is also available with the stock keymap:

1. Hold RAISE (right thumb key), then hold the left Ctrl thumb key to reach ADJUST.
2. Tap the base-layer E position to select USB output.
3. Tap the base-layer W position to unlock Studio, then connect/select KLOR in Studio.
4. Edit the keymap and save the changes to the keyboard.

Studio changes are stored on the keyboard, not written back to `config/klor.keymap`.
Saved Studio mappings can override later firmware keymap changes; use Studio's
Restore Stock Settings action when you want to return to the compiled keymap.
Combos, behavior definitions, and encoder rotation bindings remain configured in
source files. The physical layout is schematic, not an exact drawing of the PCB.
