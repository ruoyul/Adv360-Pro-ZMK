# Customization Notes

Personal notes on ZMK features to explore. Ordered by impact.

## Current state

- Mac modifier layout on thumb cluster (Cmd/Opt/Ctrl/Cmd matching keycap legends)
- Up/down arrow swap
- Delete key → Left Control
- Hyper key: hold right-inner thumb (Cmd legend) = Shift+Ctrl+Opt+Cmd
- Caps Word: tap the Caps key (bottom row, between `` ` `` and `←`), next word
  is ALL_CAPS, auto-exits on space
- Nav layer: hold Space → HJKL = arrows, YUIO = Home/PgDn/PgUp/End

## Features to explore

### 1. Home row mods (biggest change, real learning curve)

Tap F = f, hold F = Cmd. Same for A/S/D/J/K/L/; with Shift/Ctrl/Opt/Cmd.
Modifiers without leaving home position.

**Honest caveats:**
- Timing-based, no meta key. Disambiguated by press duration + overlap.
- Fast typers hit "rolling" misfires: typing "fo" fast can trigger ⌘O instead.
- Tuning knobs: `tapping-term-ms`, `flavor`, `require-prior-idle-ms`. Fiddly.
- ~2 week adaptation. Some people never adapt and rip it out. Polarizing.

**How:** `&hm LGUI F` style bindings. The `hm` behavior is already defined in
the keymap (lines 14-22), just needs to be used.

### 2. Combos

Press two keys together → third action. Common: J+K = Esc, D+F = Tab.

**How:** Add a `combos { }` block. See
[ZMK combo docs](https://zmk.dev/docs/features/combos).

## Other

- **Clique web configurator** now works (V3.0 firmware has serial support):
  https://clique.kinesis-ergo.com — quick tweaks without push/build/flash loop
- **Tenting angles:** 3 positions via foot pegs on underside
- **BT profiles 2-5:** pair to other devices, switch with Mod+2..5

## Key wear (non-concern)

Gateron Browns rated 50-100M actuations. Heavy typing ~15k/day = 9+ years to
hit rating. Home row keys are already most-used; adding mod duty replaces
reaches to dedicated modifiers, doesn't add net keystrokes. Keycap shine
happens first and is cosmetic.

## Workflow

Run `bin/sync-to-phone "commit message"` — commits, pushes, waits for Actions,
downloads the artifact, pushes `.uf2` files to the Android phone. Then unplug
phone → plug into keyboard → open Adv360 Flasher app → tap Flash Left/Right.

Bootloader: Mod+Hotkey1 (left) / Mod+Hotkey3 (right), or paperclip pinhole
in the thumb cluster gap (left: between Delete/Home/End; right: between
PgUp/Enter/PgDn).

Companion app source: `~/code/adv360-flasher`
