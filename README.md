# The Chorus Keymap

## Introduction

The Chorus Keymap was developed to sing along with the [Cantor](https://github.com/diepala/cantor)
keyboard, and for user migration from 'full size' keyboards or 100-ish key layouts, to the Cantor 42
key split keyboard, and possibly other similar split keyboards. The Cantor keyboard is made into two
parts, one part for each hand. The key layout for each hand is 3 rows per finger by 6 columns, plus
a single row of 3 thumb keys: (3 x 6 + 3) x 2 = 42 keys. The firmware flashed to the two
microcontrollers was the Vial fork of Quantum Mechanical Keyboard firmware
([Vial-QMK](https://github.com/vial-kb/vial-qmk)). Vial is based on QMK and provides a graphical way
to configure the keymap. The [Vial](https://get.vial.today/) web and desktop applications were used.

## Impossible

No, this file was typed up using the Cantor keyboard and the Chorus keymap while developing the map.
Take it one step at a time, use online keyboard testers to see which key codes are being sent or a
text file, and start slowly and patiently with an online typing tutor; also don't overdo it as your
hands will be moving in new ways.

## Usage

Using Vial Desktop:

1. File -> Save current layout... `backup.vil`
1. File -> Load layout... `cantor-chorus.vil`

## Principles to Features

The following principles are used to guide and reason about the decisions made during development of
the keymap. Features were implemented systematically following the principles, and migrating keys
from a 100 key layout. Principles are numbered, features are shown as bullet points.

1. Enable both hands, but don't require both hands:
    1. Promote touch typing;
    1. Promote relaxed posture;
    1. Promote split keyboard utilisation;
    1. Promote load sharing across hands/fingers/thumbs;
    1. Support single-handed actions;
    1. Support hand & mouse actions.
1. Enable thumbs, and a consistent control/modifier experience across layers.
1. Limit travel from home/rest to one key movement in any direction.
1. Require less long key holds.
1. Deprioritise hold for repeat - anything more than 3 repeats deserves a better method.
1. Prose first:
    - Layer 0 - Letters, Punctuation & Control:
        - LAYER SELECT, Thumb 1 Inner Tap - safely back on layer 0;
        - Start with a familiar layout (e.g. QWERTY);
        - All the keys all at once, enable N-key rollover (if supported by hardware);
        - Auto Shift, a *Deliberate* Press of keys *slightly* longer to get CAPS & Shifts;
        - Punctuation, works with Auto Shift;
        - Punctuation, ',' and '!'
        - Punctuation, '.' and '@'
        - Punctuation, \\|  ;:  '"  /?  -_
        - GUI/Menu/Win, Thumb 2 Inner Tap;
        - Surface control keys that are hit multiple times in typical use:
            - Space, Thumb 1 Resting Tap;
            - Enter, Thumb 1 Resting *Deliberate* Press;
            - Backspace, Thumb 2 Resting Tap;
            - Ctrl+Backspace, Thumb 2 Resting *Deliberate* (guard) Press;
            - Del, Thumb 1 Outer Tap;
            - Esc, Thumb 2 Outer Tap;
            - Tab, Pinky existing muscle memory.
        - Surface modifier keys:
            - *Remove* Caps Lock, often more nuisance than benefit, now even less needed;
            - Well OK, tap Shift 3 times to lock it until tapped again (ALL THE CAPS);
            - Left Shift, moves up to Pinky on the home row - ah that's better;
            - Left Shift, tap and go One-Shot Modifier (OSM);
            - Left Ctrl, tap and go One-Shot Modifier (OSM);
            - Left Ctrl, remains below Left Shift for muscle memory of selection & shortcuts;
            - Retain consistent Ctrl+Shift modifiers also for Selection Layer;
            - Left Alt, for Alt+Tab, Thumb 2 Inner Hold.
1. Fast access to more:
    - Layer 1 - Symbols, Arrows & Selection.
        - LAYER SELECT, Thumb 1 Inner *Deliberate* Press.
        - Symbols cluster on left hand;
        - Arrows, Home/End, Page Up/Down cluster on right hand;
        - Retain consistent Ctrl+Shift modifiers also for Selection Layer.
        - Dedicated Cut, Copy, Paste keys.
        - Right Alt, covers Left Alt, because some software like virtual machines use it;
        - Menu, covers GUI, as another variation/option.
    - Layer 2 - Number Pad and Function keys.
        - LAYER SELECT, Thumb 1 Outer *Deliberate* Press;
        - Let's learn to use the num pad on the left hand, if we mouse on the right?
        - Function keys cluster on right hand.
        - Free keys to use for multimedia etc.
    - Layer 3 - Free to use for multimedia etc.

Notes:

    Inner - Inner for that hand, not the keyboard pair.
    Outer - Outer for that hand, not the keyboard pair.

## Tap-Hold Concepts

Terminology in logical order:

    Tap - press and release (e.g. ≤180 ms)
    Short hold - press *slightly* longer and release (e.g. >180 ms)
    Long hold - press and hold (e.g. >200 ms)

The example times shown are known in QMK as the Tapping Term (time in milliseconds). A press and
release in less than the time is a 'tap' (e.g. ≤180 ms), anything longer/slower is a 'hold'. A tap
should feel like a rapid press and release; a short hold should feel like a more *deliberate* press
to just exceed the short hold time. Long(er) tapping terms may be used to guard against accidental
activation of the hold function (e.g. 200 ms), or to allow more time for multiple tap actions to
complete (e.g. 400 ms).