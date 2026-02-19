# Skycraft (Skyblock-style) Mod for Minicraft GBA

Skycraft is a mod of [Vulcalien's excellent Minicraft GBA port](https://github.com/Vulcalien/minicraft-gba) (vanilla/latest unmodded build: [Minicraft GBA 1.3](https://github.com/Vulcalien/minicraft-gba/releases/tag/1.3)).  
It aims to recreate the “Skyblock / SkyFactory” vibe from Minecraft: you begin with almost nothing in an endless void, and you bootstrap an entire world by carefully growing resources, crafting upgrades, and expanding your platform one block at a time.

## What changes compared to regular Minicraft?

- **Skyblock start:** You spawn in the void on a small wooden platform with a single patch of dirt and a dirt tree. There’s no surrounding land to mine. Your early game is all about steadily expanding your safe area.
- **Starter kit:** You begin with a few purpose-built items to kickstart progression:
  - **Time Wand** — speeds up saplings aging into trees when you hit them with it, helping you reduce early-game waiting.
  - **Basic Crafting Bench** — a limited bench that can only craft an *Advanced Crafting Bench*, nudging you into the intended upgrade path.
  - **Power Glove** — lets you lift and move furniture, making it easier to reorganize tight builds and early workspaces.
- **Special tree progression loop:** Progress revolves around crafting and growing increasingly valuable tree types (**dirt → sand and stone → iron → gold → gem**) each producing its matching resource/block.  
  To unlock the next tier, you craft new **acorns** by combining an existing acorn with additional ingredients, then plant and grow that new tree to start producing the next resource tier.
- **Adjusted placement rules (so building in the void is actually possible):**
  - You can place **wood** directly on the void (so you can bridge out and expand platforms).
  - You can place **stone** on top of **dirt/grass/farmland** (so you can reinforce and upgrade your base as you progress).
- **Vertical progression with stairs:**
  - Craft **stairs down** with **4 iron**. They must be placed in a **dirt hole**.
  - Craft **stairs up** with **4 gold**. They can be placed on **dirt/grass/farmland**.

Hopefully you enjoy the alpha build! If you spot any errors or issues, please report them.

---

# Minicraft for GBA

This is a demake of Minicraft by Markus Persson (aka Notch), a game made
for Ludum Dare 22 in two days.

My aim is to make a version that is as close as possible to the
original. Of course, the GBA has some hardware limitations but, since
the game isn't too complex, I could port it without too many problems.
When the limitations were impossible to overcome, I had to hack a few
things, change others, put limits and so on.

To improve the gameplay experience, I also added these features:
- a pause menu
- saving and loading the world
- a way to respawn, with or without keeping the inventory

## Differences due to Hardware limitations
|                | Original | GBA Demake |
| -------------- | :------: | :--------: |
| World size     | 128x128  | 112x112    |
| Entity limit   | ∞        | 255        |
| Chest limit    | ∞        | 32         |
| Inventory size | ∞        | 128        |

### Game Light
The light system is completely different, both visually and in how it
works. The original Minicraft calculates the light for **each pixel**:
that is, for various reasons, impractical to do on the GBA.

So I had to find another way, and the best one seemed to use tiles,
because the GBA is very good at handling them. That gives light a
'blocky' look, but it seems acceptable.

## Running
Download or build the ROM (`.gba` extension). Then open it with your GBA
emulator of choice. If you don't have one, I highly recommend mGBA.

If you have any trouble with the save files, try to manually set the
save format to `128 KB Flash ROM`.

### Performance Overlay
By holding the `L` and `R` buttons down and then pressing `Select`, the
performance overlay is enabled.\
Four hexadecimal values and two decimal values are written at the top of
the screen:
```
FF <--- vcount after 'tick'     entity count ---> FF
FF <--- vcount after 'draw'     sprite count ---> FF

60 <--- tps (ticks per second)
60 <--- fps (frames per second)
```

## Building
To build the game, I use the `Makefile` present in the files.
You will need the gcc-arm-none-eabi compiler and Python 3.

First, run `make res` to convert the necessary resources. Then, run
`make` to build the ROM.

## License
The original game `Minicraft` was made by Markus Persson in 2011.
I do not own it, nor am I affiliated to it.

This demake of the game is released under the GNU General Public
License, either version 3 of the License or any later version.
