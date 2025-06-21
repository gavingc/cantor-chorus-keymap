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

No, this document was typed up using the 42 key Cantor keyboard and the Chorus keymap while
developing the keymap. Take it one step at a time, use a text file or online keyboard testers to see
which key codes are being sent, and start slowly and patiently with an online typing tutor. 

Don't overdo it initially as your hands will be moving in new ways, and it will take some time to
build up new flexibility, stamina, and strength. Using multiple different keyboards and pointing
devices throughout a session/day/week may directly address the repetitive aspect of repetitive
strain injury (RSI). You are now, more than ever, enabled and responsible for managing your own
ergonomics and any RSI - if something doesn't feel good or hurts change it!

## Usage

Using Vial Desktop:

1. File -> Save current layout... `backup.vil`
1. File -> Load layout... `cantor-chorus.vil`

Loading the keymap provides full access to the implementation. Making a backup first allows a
previous keymap to be restored.

## Tap-Hold Concepts

Developing some tap and hold concepts is necessary to facilitate a discussion and understanding of
the keymap principles and features that follow.

The example times shown below are known in QMK as the Tapping Term *TT* in milliseconds. The actual
time *t* is also in milliseconds. A key press and release within *TT* is a Tap *t* ≤ *TT* (e.g. *t*
≤ 180 ms), anything longer/slower to release is a Hold in QMK.

When using the Chorus keymap, a Tap is a rapid press and release. A *slightly* slower release that
just exceeds the short *TT* time feels more like a *Deliberate* Press - for example when using Auto
Shift to either get an 'a' or 'A', or to get Layer 0 or Layer 1. The difference *dt* is only a few
10s of milliseconds either side of *TT* (e.g. *t* = 180 + *dt* ms). Long(er) *TT* values may be used
to guard against accidental activation of the hold function (e.g. *TT* = 200 ms), or to allow more
time to complete multiple tap actions (e.g. *TT* = 400 ms).

Chorus keymap terminology in logical order:

    Tap - rapid press and release (e.g. *t* ≤ 180 ms)
    *Deliberate* Press - press *slightly* longer and release (e.g. *t* = 180 + *dt* ms)
    *Deliberate* (guard) Press - press *slightly* longer still and release (e.g. *t* = 200 + *dt* ms)
    Hold - press and hold while doing another action (e.g. Ctrl + P)
    Long Hold - press that must be held indefinitely while performing other actions.

## Principles to Features

The following principles are used to guide and reason about the decisions made during development
and implementation of the keymap. Features were implemented systematically following the principles,
and migrating keys from a 100 key layout.

Principles are numbered, features are shown as bullet points:

1. Enable both hands, but don't require both hands:
    1. Promote touch typing - reduce strain from looking down, and increase work flow and
       productivity;
    1. Promote relaxed posture - reduce tension;
    1. Promote split keyboard utilisation - open chest/easier breathing/reduce hunching over;
    1. Promote load sharing across hands/fingers/thumbs;
    1. It's OK to move the whole hand occasionally from the home row, it adds movement and reduces
       static holds;
    1. Support single-handed actions;
    1. Support hand & mouse actions.
1. Enable thumbs, and a consistent control/modifier experience across layers.
1. Limit finger travel from home/rest positions during prose to one key movement in any direction.
1. Reduce Long Holds:
    - Tap and *Deliberate* Press for layers (not Long Hold).
    - One Shot Modifiers, Tap Shift when needed (no need to Hold for many cases, and prefer Auto
      Shift).
    - Tip: Ctrl (Hold) + p (Tap) versus 
    - Tip: Ctrl (Hold) + p (*Deliberate* Press) -> Ctrl+Shift+P
1. Eliminate finger/hand contortions:
    - *Move* Left Ctrl key, Thumb 2 Outer on Hold - especially for high frequency combinations with a/z/x/c/v/n/p.
1. Deprioritise hold for repeat - anything more than 3 repeats deserves a better method.
1. Prose first:
    - Layer 0 - Letters, Punctuation & Control:
        - LAYER SELECT, Thumb 1 Inner Tap - safely back on Layer 0;
        - Start with a familiar layout (e.g. QWERTY);
        - All the keys all at once, enable N-key rollover (as supported by hardware);
        - Auto Shift, a *Deliberate* Press of keys *slightly* longer to get CAPS & Shifted Punctuation;
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
        - Modifier keys:
            - *Remove* Caps Lock key, often more nuisance than benefit, now even less needed;
            - Left Shift, well OK tap Shift 3 times to lock it pressed until tapped again (ALL THE CAPS);
            - Left Shift, moves up to Pinky on the home row - ah that's better;
            - Left Shift, tap and go One Shot Modifier (OSM);
            - *Move* Left Ctrl key, Thumb 2 Outer on Hold;
            - Retain consistent Ctrl+Shift modifiers also for Selection Layer;
            - Left Alt, for Alt+Tab, Thumb 2 Inner on Hold.
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
        - Number pad cluster on the left hand if we mouse on the right?
        - Function keys cluster on right hand.
        - Free keys to use for multimedia etc: mute, vol-, vol plus.
    - Layer 3 - Free to use for multimedia etc.

Notes:

    Inner - Inner for that hand, not the keyboard pair.
    Outer - Outer for that hand, not the keyboard pair.
    Left Hand Pinky Bottom Row - Key disabled because it can cause wrist pain, enable if you want it.