---
title: "Sprite (Concept) - Giant Bomb"
source: "https://www.giantbomb.com/sprite/3015-491/"
author:
  - "[[Giant Bomb]]"
published:
created: 2025-02-08
description: "A two-dimensional image or animation overlaid into a scene. The foundation of early 2D games, making up everything from props to the player-controlled character."
tags:
  - "clippings"
---
Sprite last edited by [PlamzDooM](https://www.giantbomb.com/profile/plamzdoom/) on 12/03/24 09:31PM [View full history](https://www.giantbomb.com/sprite/3015-491/wiki-history/)

## Overview

A sprite is a two-dimensional ([2D](https://www.giantbomb.com/2d/3015-1427/)) bitmap graphic object that can be a static image or animation that is integrated into a larger scene. Sprites are used in games to collectively create a scene. Each sprite is used to represent each object. A "Sprite Sheet" is simply a collection of still images that progress. Once displayed sequentially it creates animation.

Sprites can be used for [two-dimensional](https://www.giantbomb.com/2d/3015-1427/) games, or [pseudo-3D](https://www.giantbomb.com/25d/3015-660/) [sprite-scaling](https://www.giantbomb.com/sprite-scaling/3015-7122/) (such as [Super Scaler](https://www.giantbomb.com/super-scaler/3015-8389/), [Mode 7](https://www.giantbomb.com/mode-7/3015-184/) and [Ray Casting](https://www.giantbomb.com/ray-casting/3015-1517/)), or [pre-rendered](https://www.giantbomb.com/pre-rendered-movement/3015-5983/) games.

Sprites can also be used for, and have been used in, three-dimensional games. The way that they are typically used within [3D](https://www.giantbomb.com/polygonal-3d/3015-1430/) games is through rendering or imitating a rendered frame from certain perspectives. This removes the computational overhead of rendering each position dynamically. Sprites are also often used in 3D games today to display [grass](https://www.giantbomb.com/grass/3055-198/) and foliage, in the form of [billboarding](https://www.giantbomb.com/billboarding/3015-5074/). Sprites can also be used in conjunction with [cel-shading](https://www.giantbomb.com/cel-shading/3015-173/).

In recent years, sprites have been used beyond gaming, such as CSS sprites which are used in [web design](https://www.giantbomb.com/online/3015-559/ "Web design (page does not exist)") as a way to improve performance by combining numerous small images or icons into a larger image called a sprite sheet or tile set, and selecting which icon to show on the rendered page using Cascading Style Sheets.

## Sprite Drawing Methods

The following are the two most common methods for drawing sprites.

### Buffering / Blitting

Using the buffering method, or blitting method, the CPU (central processing unit) and/or GPU (graphics processing unit) modify a frame-buffer held in RAM (random-access memory), which requires more memory cycles to load and store the pixels and refresh the backgrounds behind moving objects. The sprites are usually processed through a display list. This method frequently requires double buffering to avoid flickering and tearing, but place fewer restrictions on the size and number of moving objects.

This method is ideal for systems with high processing power (a fast CPU and/or GPU), and/or a high amount of fast RAM memory. However, it was usually only [arcade](https://www.giantbomb.com/arcade/3045-84/) systems that were capable of using this method very effectively up until the early 1990s (such as [Sega](https://www.giantbomb.com/sega/3010-62/)'s [Super Scaler](https://www.giantbomb.com/super-scaler/3015-8389/) systems), due to their expensive CPU, GPU and RAM technologies. A number of [personal computers](https://www.giantbomb.com/pc/3045-94/) also used this method in the 1980s (such as the [Amiga](https://www.giantbomb.com/amiga/3045-1/)), as well as a few consoles (such as the [Atari 7800](https://www.giantbomb.com/atari-7800/3045-70/)), but due to limited processing power and memory at the time, these systems were often unable to match the quality of hardware sprites without suffering slowdowns. But as processors and memory technology improved, buffering/blitting became the most common method for drawing sprites in the mid-1990s, for both personal computers and home consoles (such as the [Sega Saturn](https://www.giantbomb.com/saturn/3045-42/)).

### Hardware Sprites

![Mega Man sprite](https://www.giantbomb.com/a/uploads/original/0/4/11193-megaman.jpg)

Mega Man sprite

Hardware sprites, rather than being part of the bitmap data in the frame-buffer, instead float around on top without affecting the data in the frame-buffer below, much like a ghost or "sprite". Using this method, there is a defined limit to the number of sprites on screen and their sizes, but two-dimensional shapes could be moved around the screen horizontally and vertically with minimal software overhead. In other words, hardware sprites have very little impact on overall system performance.

This method was ideal for systems with limited processing power and RAM memory. It was the most commonly used method for classic home consoles in the 1980s and early 1990s (such as the [Sega Mega Drive/Genesis](https://www.giantbomb.com/genesis/3045-6/) and [Super Nintendo Entertainment System](https://www.giantbomb.com/super-nintendo-entertainment-system/3045-9/)), some arcade systems in the early 1980s (such as the [Namco Pac-Man](https://www.giantbomb.com/pac-man/3030-7624/)), the more advanced personal computers of the 1980s (such as the [Sharp X68000](https://www.giantbomb.com/sharp-x68000/3045-95/)), and handheld systems up until the 2000s (such as the [Game Boy Advance](https://www.giantbomb.com/game-boy-advance/3045-4/)). But as processing power and RAM memory improved, the use of hardware sprites eventually fell into disuse in the mid-1990s, though it continued for handhelds up until the 2000s.

## History

### 1970s

The first video games did not use sprites. [Pong](https://www.giantbomb.com/pong/3030-22195/), for example, when it released in 1972, used simple rectangular blocks and lines to display the ball, paddles and points. The use of sprites became possible with the use of ROM (read-only memory) for several [arcade](https://www.giantbomb.com/arcade/3045-84/) games in 1974.

![Basketball, released by Taito for arcades in 1974. It was the first game to use sprites.](https://www.giantbomb.com/a/uploads/scale_small/13/139866/2698167-1104-021641.jpg)

Basketball, released by Taito for arcades in 1974. It was the first game to use sprites.

[Taito](https://www.giantbomb.com/taito-corporation/3010-135/ "Taito") released the earliest video games with sprites in 1974. The first game to use sprites was [Basketball](https://www.giantbomb.com/basketball/3030-36540/ "List of Taito games (page does not exist)"), a sports game released in [Japan](https://www.giantbomb.com/japan/3035-37/) by Taito in early 1974 and imported to [North America](https://www.giantbomb.com/north-america/3035-1664/) by [Midway](https://www.giantbomb.com/midway-games/3010-185/) as TV Basketball in February 1974. Basketball represented four [basketball](https://www.giantbomb.com/basketball/3055-438/) players as well as two baskets as sprite images. These basketball players were the first [player characters](https://www.giantbomb.com/player-character/3015-968/) and the [first representation](http://allincolorforaquarter.blogspot.co.uk/2013/11/video-game-firsts.html) of [humans](https://www.giantbomb.com/human/3015-810/) in gaming history.

*[Speed Race](https://www.giantbomb.com/speed-race/3030-36499/ "Speed Race")*, which was designed by [Tomohiro Nishikado](https://www.giantbomb.com/tomohiro-nishikado/3040-55262/) and ran on [Taito Discrete Logic](http://www.system16.com/hardware.php?id=625) hardware, released shortly afterwards in 1974. It [featured sprites](http://vintage3d.org/history.php) with collision detection, moving along a [vertical scrolling](https://www.giantbomb.com/vertical-scrolling/3015-1899/) playfield (see Bill Loguidice & Matt Barton*, Vintage games: an insider look at the history of Grand Theft Auto, Super Mario, and the most influential games of all time*, page 197, 2009).

The [Fujitsu MB14241](http://gaming.wikia.com/wiki/Video_display_controller "Video display controller") was used to accelerate the drawing and buffering of sprite graphics for various 1970s arcade games from [Taito](https://www.giantbomb.com/taito-corporation/3010-135/ "Taito") and [Midway](https://www.giantbomb.com/midway-games/3010-185/ "Midway Games"), such as *[Gun Fight](https://www.giantbomb.com/gun-fight/3030-32574/ "Gun Fight")* (1975), *[Sea Wolf](https://www.giantbomb.com/sea-wolf/3030-10752/ "Sea Wolf (video game)")* (1976) which ran on the [Midway 8080](https://www.giantbomb.com/heretic/3035-2541/) hardware ([ref](https://github.com/mamedev/mame/tree/master/src/mame/drivers/mw8080bw.c)), and the blockbuster hit *[Space Invaders](https://www.giantbomb.com/space-invaders/3030-5099/ "Space Invaders")* (1978). The [Taito 8080](http://system16.com/hardware.php?id=629) hardware engineered by [Tomohiro Nishikado](https://www.giantbomb.com/tomohiro-nishikado/3040-55262/) for *Space Invaders*, which also used the Fujitsu MB14241 ([ref](https://github.com/mamedev/mame/tree/master/src/mame/drivers/8080bw.c)), could display up to 11 sprites per scanline (see [here,](http://books.google.co.uk/books?id=oK3D4i5ldKgC&pg=PA173) [here](http://www.computerarcheology.com/wiki/wiki/Arcade/SpaceInvaders) and [here](http://www.vasulka.org/archive/Writings/VideogameImpact.pdf#page=24) for more information).

In 1977, the [Taito Z80](http://system16.com/hardware.php?id=628 "Arcade system board") [arcade system board](http://gaming.wikia.com/wiki/Arcade_system_board "Arcade system board") used for *[Super Speed Race](https://www.giantbomb.com/super-speed-race-v/3030-41059/ "Speed Race")* was capable of generating up to 16 sprites in hardware and display 4 sprites per scanline. Each sprite could have a size up to 32 pixels in width or height and display up to 15 colors (see references [here](https://github.com/mamedev/mame/tree/master/src/mame/drivers/sspeedr.c), [here](http://web.archive.org/web/20130104202755/http://mamedev.org/source/src/mame/video/sspeedr.c.html) and [here](http://books.google.co.uk/books?id=TEp5AgAAQBAJ&pg=PT253)).

![Galaxian, released by Namco for arcades in 1979. Its Namco Galaxian hardware, featuring multi-colored sprites, was widely used during the early 1980s.](https://www.giantbomb.com/a/uploads/scale_small/13/139866/2697361-1031-031956.jpg)

Galaxian, released by Namco for arcades in 1979. Its Namco Galaxian hardware, featuring multi-colored sprites, was widely used during the early 1980s.

The [Namco Galaxian](http://gaming.wikia.com/wiki/Namco_Galaxian "Namco Galaxian") arcade system, developed by Namco for the 1979 arcade hit *[Galaxian](https://www.giantbomb.com/galaxian/3030-2445/)*, used specialized graphics hardware supporting RGB color, multi-colored sprites and tilemap backgrounds. It could display up to 15 hardware sprites across each scanline. Each sprite could be up to 16x16 pixels in size, with 3 colors each.<sup><a href="https://github.com/mamedev/mame/tree/master/src/mame/video/galaxian.c" rel="nofollow " data-ref-id="false">[1]</a></sup> The Namco Galaxian hardware was widely used during the [golden age of arcade video games](http://gaming.wikia.com/wiki/Golden_age_of_arcade_video_games "Golden age of arcade video games"), by game companies such as [Namco](https://www.giantbomb.com/namco/3010-7420/ "Namco"), [Centuri](https://www.giantbomb.com/centuri-inc/3010-1456/ "Centuri"),[Gremlin](https://www.giantbomb.com/gremlin-industries/3010-7000/ "Gremlin Industries (page does not exist)"), [Irem](https://www.giantbomb.com/irem-corp/3010-461/ "Irem"), [Konami](https://www.giantbomb.com/konami-corporation/3010-87/ "Konami"), [Midway](https://www.giantbomb.com/midway-games/3010-185/ "Midway Games"), [Nichibutsu](https://www.giantbomb.com/nihon-bussan-co-ltd/3010-249/ "Nichibutsu"), [Sega](https://www.giantbomb.com/sega/3010-62/ "Sega") and [Taito](https://www.giantbomb.com/taito-corporation/3010-135/ "Taito Corporation") (see references [here](https://github.com/mamedev/mame/tree/master/src/mame/drivers/galaxian.c) and [here](https://web.archive.org/web/20140103070737/http://mamedev.org/source/src/mame/drivers/galdrvr.c.html)).

### 1980s to 1990s

In the 1980s, [sprite-scaling](https://www.giantbomb.com/sprite-scaling/3015-7122/ "2.5D") became a popular technique in [arcade](https://www.giantbomb.com/arcade/3045-84/) games to represent a [three-dimensional](https://www.giantbomb.com/polygonal-3d/3015-1430/) perspective using [2D](https://www.giantbomb.com/2d/3015-1427/) sprite graphics, i.e. [pseudo-3D](https://www.giantbomb.com/25d/3015-660/) graphics.

![After Burner, released by Sega for arcades in 1987. Its Super Scaler technology featured advanced sprite scaling and rotation capabilities.](https://www.giantbomb.com/a/uploads/scale_small/13/139866/2722035-1212-031335.jpg)

After Burner, released by Sega for arcades in 1987. Its Super Scaler technology featured advanced sprite scaling and rotation capabilities.

[Sega](https://www.giantbomb.com/sega/3010-62/ "Sega") in particular was at the forefront of sprite-scaling graphics with its powerful custom [Super Scaler](https://www.giantbomb.com/super-scaler/3015-8389/) graphics boards, which could quickly scale and rotate many large colourful sprites at high frame rates. Sega's Super Scaler hardware powered a string of 1980s arcade hits, such as [Hang-On](https://www.giantbomb.com/hang-on/3030-11570/) and [Space Harrier](https://www.giantbomb.com/space-harrier/3030-6036/ "Space Harrier") in 1985, and [Out Run](https://www.giantbomb.com/outrun/3025-464/ "Out Run") in 1987. Sega introduced sprite rotation with [After Burner](https://www.giantbomb.com/after-burner/3025-21/ "After Burner") in 1987, and went on to produce more hits, such as [Galaxy Force](https://www.giantbomb.com/galaxy-force/3025-2896/ "Galaxy Force"), [Power Drift](https://www.giantbomb.com/power-drift/3030-7440/) and [Last Survivor](https://www.giantbomb.com/last-survivor/3030-40567/) in 1988.

Other arcade manufacturers such as [Namco](https://www.giantbomb.com/namco/3010-7420/ "Namco"), [Capcom](https://www.giantbomb.com/capcom/3010-367/ "Capcom") and [SNK](https://www.giantbomb.com/snk-playmore/3010-616/ "SNK") also relied on custom graphics processors in order to produce similarly advanced sprite graphics in the 1980s to early 1990s. Eventually, the [Sega Saturn](https://www.giantbomb.com/saturn/3045-42/) console, released in 1994, was able to rival the sprite graphics of the arcades. Along with its arcade counterpart, the Sega ST-V, the Saturn had the most advanced sprite capabilities of the 1990s.

Following the rise of true [3D polygon](https://www.giantbomb.com/polygonal-3d/3015-1430/) graphics in the early-mid-1990s, the sprite graphics, including the sprite-scaling technique, eventually declined in popularity.

## Hardware Capabilities

This is a table listing the sprite capabilities of various classic gaming systems and/or graphics chips.

For the sprite scaling/zooming and rotation/mirroring capabilities of these systems and chips (the ones with hardware support for these features), see [here](https://www.giantbomb.com/sprite-scaling/3015-7122/). For a full detailed table of sprite capabilities, with references, see [here](http://gaming.wikia.com/wiki/Sprite#Hardware_sprites).

| **Systems / [Chips](http://gaming.wikia.com/wiki/Graphics_processing_unit)** | **Year** | **Sprites on screen** | **Sprites on line** | **[Texels](https://en.wikipedia.org/wiki/Texel_\(graphics\)) on line** | **Texture width** | **Texture height** | **[Colors](http://gaming.wikia.com/wiki/Two-dimensional) per sprite** | **Back-ground** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [Fujitsu MB14241](http://gaming.wikia.com/wiki/Video_display_controller#List_of_example_VDCs) | 1975 | 60 | 9 | 144 | 4 to 32 | 1 to 224 | 1 | 1 bitmap layer |
| [Fairchild Channel F](https://www.giantbomb.com/channel-f/3045-66/) | 1976 | Display list (run by CPU) | 9 | 56 | 4, 8 | 5, 8 | 1 | 1 bitmap layer |
| [Atari 2600](https://www.giantbomb.com/atari-2600/3045-40/) | 1977 | 9 (5 multiplied by CPU) | 9 (with triplication) | 51 (with triplication) | 1, 8 | 192 | 1 | 1 bitmap layer |
| [Taito Z80](http://www.system16.com/hardware.php?id=628) | 1977 | 7 | 7 | 224 | 32 | 16 | 15 | 1 tile or bitmap layer |
| [Atari 8-Bit](https://www.giantbomb.com/atari-8-bit/3045-24/) & [5200](https://www.giantbomb.com/atari-5200/3045-67/) | 1979 | Display list | 8 | 40 | 2, 8 | 128, 256 | 1, 3 | 1 bitmap layer |
| [Namco Galaxian](http://gaming.wikia.com/wiki/Namco_Galaxian) | 1979 | Display list | 15 | 240 | 8, 16 | 8, 16 | 3 | 1 tile layer and 1 bitmap layer |
| [ColecoVision](https://www.giantbomb.com/colecovision/3045-47/), [MSX](https://www.giantbomb.com/msx/3045-15/), [Sega SG-1000](https://www.giantbomb.com/sega-sg-1000/3045-141/) | 1979 | 32 | 4 | 64 | 8, 16 | 8, 16 | 1 | 1 tile layer |
| [Namco Pac‑Man](https://www.giantbomb.com/pac-man/3030-7624/) | 1980 | 8 | 8 | 128 | 16 | 16 | 3 | 2 tile layers |
| [Sega G80](http://gaming.wikia.com/wiki/Sega_G80) | 1981 | 64 | 32 | 256 | 8, 16 | 8, 16 | 3 | 2 tile layers |
| [Sega VCO Object](http://gaming.wikia.com/wiki/Sega_VCO_Object) | 1981 | 64 | 16 | 315 | 8 to 20 | 8 to 20 | 3, 7 | 1 tile layer and 1 bitmap layer |
| [Commodore 64](http://gaming.wikia.com/wiki/Sega_VCO_Object) | 1982 | Display list (run by CPU) | 8 | 96, 192 | 12, 24 | 21 | 1, 3 | 1 tile or bitmap layer |
| [Namco Pole Position](https://en.wikipedia.org/wiki/Namco_Pac-Man) | 1982 | 64 | 32 | 512 | 16, 32 | 16, 32 | 15 | 1 tile layer and 1 bitmap layer |
| [Sega 315‑5011 & 315‑5012](http://gaming.wikia.com/wiki/List_of_Sega_arcade_system_boards) | 1982 | 128 | 100 | 800 | 8 to 256 | 8 to 256 | 15 | 2 tile layers and 1 bitmap layer |
| [Famicom / NES](https://www.giantbomb.com/nintendo-entertainment-system/3045-21/) | 1983 | 64 | 8 | 64 | 8 | 8, 16 | 3 | 1 tile layer |
| [Atari 7800](https://www.giantbomb.com/atari-7800/3045-70/) | 1984 | 100 (without back-ground) | 30 (without back-ground) | 160 | 4 to 160 | 4, 8, 16 | 1, 3, 8 | 1 bitmap layer |
| [Amiga](https://www.giantbomb.com/amiga/3045-1/) ([OCS](https://en.wikipedia.org/wiki/Original_Chip_Set)) | 1985 | Display list | 8 | 128 | 16 | Up to 256 | 3, 15 | 2 bitmap layers |
| [Sega Master System](https://www.giantbomb.com/sega-master-system/3045-8/) & [Game Gear](https://www.giantbomb.com/game-gear/3045-5/) | 1985 | 64 | 8 | 128 | 8, 16 | 8, 16 | 15 | 1 tile layer |
| [MSX2](https://www.giantbomb.com/msx/3045-15/) | 1985 | 32 | 8 | 128 | 8, 16 | 8, 16 | 1, 3, 7, 15 per line | 1 tile or bitmap layer |
| [Sega OutRun](http://gaming.wikia.com/wiki/OutRun) | 1986 | 128 | 128 | 1600 | 8 to 512 | 8 to 256 | 15 | 2 tile layers and 1 bitmap layer |
| [Namco System 2](http://gaming.wikia.com/wiki/Namco_System_2) | 1987 | 128 | 128 | 2081 | 8 to 64 | 8 to 64 | 255 | 7 tile layers and 1 bitmap layer |
| [PC-Engine / TurboGrafx-16](https://www.giantbomb.com/turbografx-16/3045-55/) | 1987 | 64 | 16 | 256 | 16, 32 | 16, 32, 64 | 15 | 1 tile layer |
| [Sharp X68000](https://www.giantbomb.com/sharp-x68000/3045-95/) | 1987 | 512 (128 multiplied by raster interrupt) | 32 | 512 | 16 | 16 | 15 | 1-2 tile layers and 1-4 bitmap layers |
| [Sega X Board](http://gaming.wikia.com/wiki/After_Burner) | 1987 | 256 | 256 | 3200 | 8 to 512 | 8 to 256 | 15 | 4 tile layers and 1 bitmap layer |
| [Taito Ninja Warriors](https://www.giantbomb.com/the-ninja-warriors/3030-1618/) | 1987 | 128 | 108 | 1737 | 16 | 16 | 15 | 6 tile layers |
| [Taito Z System](http://gaming.wikia.com/wiki/Taito_Z_System) | 1987 | 512 | 108 | 1737 | 16 to 128 | 8 to 128 | 15 to 255 | 2-4 tile layers and 1 bitmap layer |
| [Capcom CPS](http://gaming.wikia.com/wiki/CP_System) | 1988 | 256 | 65 | 1048 | 16 to 256 | 16 to 256 | 15 | 3 tile layers and 2 bitmap layers |
| [Sega System 24](http://gaming.wikia.com/wiki/Sega_System_24) | 1988 | 2048 | 512 | 4096 | 8 to 1024 | 8 to 1024 | 15 to 255 | 4 tile layers |
| [Sega Y Board](http://gaming.wikia.com/wiki/Sega_Y_Board) | 1988 | 2176 | 400 | 3200 | 8 to 512 | 8 to 512 | 15 to 511 | 1 bitmap layer |
| [Taito B System](http://gaming.wikia.com/wiki/Taito_B_System) | 1988 | 408 | 110 | 1768 | 16 to 256 | 16 to 256 | 15 to 63 | 2 tile layers and 1 bitmap layer |
| [MSX2+ & MSX TurboR](https://www.giantbomb.com/msx/3045-15/) | 1988 | 32 | 8 | 128 | 8, 16 | 8, 16 | 1, 3, 7, 15 per line | 1 tile layer and 1 bitmap layer |
| [Sega Mega Drive / Genesis](https://www.giantbomb.com/genesis/3045-6/) | 1988 | 80 | 20 | 320 | 8, 16, 24, 32 | 8, 16, 24, 32 | 15 | 2 tile layers |
| [Fujitsu FM Towns](https://www.giantbomb.com/fm-towns/3045-108/) | 1989 | 1024 | 64 | 1024 | 16 | 16 | 15 | 1-2 bitmap layers |
| [Game Boy](https://www.giantbomb.com/game-boy/3045-3/) | 1989 | 40 | 10 | 80 | 8 | 8, 16 | 3 | 1 tile layer |
| [SuperGrafx](https://www.giantbomb.com/supergrafx/3045-119/) | 1989 | 128 | 32 | 512 | 16, 32 | 16, 32, 64 | 15 | 2 tile layers |
| [Amstrad Plus](https://www.giantbomb.com/amstrad-cpc/3045-11/) | 1990 | Display list (run by CPU) | 16 | 256 | 16 | 16 | 15 | 1 bitmap layer |
| [Neo Geo](https://www.giantbomb.com/neo-geo/3045-25/) | 1990 | 384 | 96 | 1536 | 16 | 16 to 512 | 15 | 1 tile layer |
| [Sega System 32](http://gaming.wikia.com/wiki/Sega_System_32) | 1990 | 8192 | 512 | 4096 | 8 to 1024 | 8 to 1024 | 15 to 512 | 4 tile layers and 1 bitmap layer |
| [Super Famicom & SNES](https://www.giantbomb.com/super-nintendo-entertainment-system/3045-9/) | 1990 | 128 | 34 | 272 | 8, 16, 32, 64 | 8, 16, 32, 64 | 15 | 1-4 tile layers or 1 affine mapped tile layer |
| [Amiga](https://www.giantbomb.com/amiga/3045-1/) ([AGA](http://en.wikipedia.org/wiki/Amiga_Advanced_Graphics_Architecture)) | 1992 | Display list | 8 | 448 | 16, 32, 64 | Up to 256 | 3, 15 | 2 bitmap layers |
| [Taito SZ System](http://gaming.wikia.com/wiki/Taito_Z_System#Taito_SZ_System) | 1992 | 1024 | 162 | 2604 | 16 to 128 | 8 to 128 | 15 to 255 | 4 tile layers and 1 bitmap layer |
| [Atari Jaguar](https://www.giantbomb.com/jaguar/3045-28/) | 1993 | 1000 | 90 | 720 | 8 to 360 | Up to 220 | Up to 255 | 1 bitmap layer |
| [Capcom CPS2](https://en.wikipedia.org/wiki/CP_System_II) | 1993 | 900 | 65 | 1048 | 16 to 256 | 16 to 256 | 15 | 3 tile layers and 2 bitmap layers |
| [Sega Saturn](https://www.giantbomb.com/saturn/3045-42/) & [ST-V](http://gaming.wikia.com/wiki/Sega_ST-V) | 1994 | 16,384 | 512 | 4096 | 8 to 504 | 1 to 255 | 15 to 32,768 | 3-6 tile layers and 1-4 bitmap layers |
| [Sony PlayStation](https://www.giantbomb.com/playstation/3045-22/) | 1994 | 4000 | 128 | 1024 | 8, 16, 256 | 8, 16, 256 | 15, 255 | 1 bitmap layer |
| [Capcom CPS3](https://www.giantbomb.com/cps/3015-2020/) | 1996 | 1024 | 482 | 3861 | 8, 16 | 8, 16 | 63, 255 | 4 tile layers |
| [Data East MLC System](http://www.system16.com/hardware.php?id=950) | 1996 | 614 | 176 | 2828 | 16 | 16 | 15 to 255 | 2 tile layers |
| [Hyper Neo Geo 64](http://gaming.wikia.com/wiki/Hyper_Neo_Geo_64) | 1997 | 1535 | 384 | 3072 | 16 | 16 to 512 | 15, 255 | 4 tile layers |
| [Game Boy Advance](https://www.giantbomb.com/game-boy-advance/3045-4/) | 2001 | 128 | 128 | 1210 | 8, 16, 32, 64 | 8, 16, 32, 64 | 15, 255 | 2-4 layers or 1-2 affine layers |
| [Nintendo DS](https://www.giantbomb.com/nintendo-ds/3045-52/) | 2004 | 256 (128 per screen) | 128 | 1210 | 8, 16, 32, 64 | 8, 16, 32, 64 | 15 to 32,768 | 8 layers (4 per screen); each layer is independent |
| **Systems / Chips** | **Year** | **Sprites on screen** | **Sprites on line** | **Texels on line** | **Texture width** | **Texture height** | **Colors** | **Back-ground** |

## See Also

- [2D](https://www.giantbomb.com/2d/3015-1427/)
- [2.5D](https://www.giantbomb.com/25d/3015-660/)
- [Sprite Scaling](https://www.giantbomb.com/sprite-scaling/3015-7122/)
- [Super Scaler](https://www.giantbomb.com/super-scaler/3015-8389/)
- [Mode 7](https://www.giantbomb.com/mode-7/3015-184/)
- [Ray Casting](https://www.giantbomb.com/ray-casting/3015-1517/)