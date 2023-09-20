# ZScript HudMessage by Agent_Ash

## Components

This library requires three components to function:

1. `JGP_HudMessageHandler` class (handles the drawing)

2. `JGP_HudMessage` (handles the message itself)

3. `MAPINFO` (adds the handler)

## How to use

To draw the hud message, call `JGP_HudMessage.Create` from anywhere in play context. Currently cannot be called in UI scope.

```cs
static JGP_HudMessage Create(string text, uint id = 0, name fontname = 'NewSmallFont', int fontColor = Font.CR_Red, vector2 pos = (160, 50), int alignment = ALIGN_LEFT, uint fadeInTime = 0, uint typeTime = 0, uint holdTime = 35, uint fadeOutTime = 0, vector2 scale = (1,1), PlayerInfo viewer = null)
```

Arguments:

* `text` — the text to print. LANGUAGE references are supported.

* `id` (default: 0) — the ID of the message. If non-zero, new messages will override older messages with the same ID.

* `fontname` (default: 'NewSmallFont') — the name of the font to be used.

* `fontcolor` (default: Font.CR_Red) — the color of the font (as defined in the `Font` struct).

* `pos` (default: (160, 50)) — the position of the message in a virtual 320x200 grid. Note, this is virtual resolution, so `(0, 0)` corresponds to top left corner of the screen.

* `alignment` (default: ALIGN_LEFT) — the alignment of the text relative to the `pos`.
  
  * `JGP_HudMessage.ALIGN_CENTER` — center alignment
  
  * `JGP_HudMessage.ALIGN_LEFT` — left alignment (default)
  
  * `JGP_HudMessage.ALIGN_RIGHT` — right alignment

* `fadeInTime` (default: 0) — the time **in tics** it takes the message to fade in. If non-zero, `holdTime` will begin the countdown after the message fully faded in.

* `typeTime` (default: 0) — if non-zero, each character will take this amount of time **in tics** to type out each character in the string. If `fadeInTime` is non-zero, typing and fade-in will overlap, and `holdTime` will begin counting after whatever took longer (fade-in or type-out) has finished.

* `holdTime` (default: 35) — the time **in tics** the message will stay on the screen (fade-in, fade-out and type-out are added on top of this).

* `fadeOutTime` (default: 0) — the time **in tics** the message will take to fade out before disappearing.

* `viewer` (default: null) — a `PlayerPawn` pointer. If non-null, the message will only be visibled to the specified player. Otherwise it'll be visible to everyone.

## License

MIT License (see ZSHudmsg/LICENSE.txt).


