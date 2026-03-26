# Customization Notes

Personal notes on ZMK features to explore. Ordered by impact.

## Current state

Commit `2e113ff` has:
- Mac modifier layout on thumb cluster (Cmd/Opt/Ctrl/Cmd matching keycap legends)
- Up/down arrow swap
- Delete key → Left Control

## Features to explore

### 1. Caps Word (easiest win, ~5 min)

Replace Caps Lock with `&caps_word`. Tap it, next word is ALL_CAPS, auto-exits on
space. Great for `CONSTANT_NAMES` in code.

**Where:** `config/adv360.keymap` line 35/45, change `&kp CAPS` → `&caps_word`

### 2. Navigation layer (medium effort, big payoff)

Hold a thumb key → HJKL become arrows, plus Home/End/PgUp/PgDn nearby. Never
reach for the arrow row.

**Which key:** Space as layer-tap (`&lt NAV SPACE` — tap=space, hold=nav layer).
Or use one of the unused hotkeys (circled 1/2/3/4 in inner columns).

**How:** Add a new layer block in the keymap, bind the hold key with `&lt`.

### 3. Home row mods (biggest change, real learning curve)

Tap F = f, hold F = Cmd. Same for A/S/D/J/K/L/; with Shift/Ctrl/Opt/Cmd.
Modifiers without leaving home position.

**Honest caveats:**
- Timing-based, no meta key. Disambiguated by press duration + overlap.
- Fast typers hit "rolling" misfires: typing "fo" fast can trigger ⌘O instead.
- Tuning knobs: `tapping-term-ms`, `flavor`, `require-prior-idle-ms`. Fiddly.
- ~2 week adaptation. Some people never adapt and rip it out. Polarizing.

**How:** `&hm LGUI F` style bindings. The `hm` behavior is already defined in
the keymap (lines 14-22), just needs to be used.

### 4. Combos

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

## Workflow reminder

Edit `config/adv360.keymap` → commit → push → GitHub Actions builds → download
`firmware-clique` artifact → flash both halves (Mod+Hotkey1 for left,
Mod+Hotkey3 for right, or paperclip pinhole in thumb cluster).
