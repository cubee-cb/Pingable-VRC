## Pingable VRC

A small custom emoji system for VRChat, for notifying people of things using icons.

In its current configuration, it uses an 8x8 grid of icons (totalling 64). The first one (0) is ignored.
These are split into 4 category submenus of 15 each, with the remaining 3 in a fifth submenu. Category icons depend on GoGoLoco, they should default to the standing figure if you don't have it.
All icons are placeholder squares showing the number ID of the played icon with a border colour corresponding to the category. Sync has not been tested yet.

Stats:
- 1 particle system
- 1 material (VRChat/Mobile/Particles/Additive)
- 2 animator layers
- 1 synced int parameter (8 bytes)
- 1 2k texture (for 256x256 per icon)
It may also sync the float parameter, though it doesn't need to.

Included sound effect is the Boss Warning ping from [Ninja Cat Remewstered](https://pixelshock.itch.io/ninja-cat-remewstered).

### How it works
"pingable/ping" is set from the menu, which says which icon to spawn.
At the moment, I just have an animation that drives the Start Frame of a particle system. Its Motion time is directed by the parameter "pingable/pingFloat".
"pingable/pingFloat" is set by a VRCAvatarParamaterDriver to simply scale the value of "pingable/ping" from int 0-63 down to float 0-1.

### Known flaws
- You cannot change the icon while one is active. Ideally, it would restart the animation, but I currently have no reasonable way to detect if "pingable/ping" changed from any number to any other number. As a workaround, you can manually stop the existing one; it's just a toggle at the end of the day.
- The icon will end up ever so slightly angled, because I don't know if I can directly set the particle's rotation on a curve rather than just its velocity. I got it as close as I could tell from the editor.
