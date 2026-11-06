The Legend of Edgar 1.38 for AmigaOS 3.x
========================================

The Legend of Edgar (Parallel Realities), the 2D platform adventure: Edgar
sets out to rescue his father from the evil sorcerer, through forests,
caves, mines and a castle, with puzzles, bosses and items to find. For
AmigaOS 3.x on a 68040 or 68060 with an FPU and an RTG screen, on
OpenGPU's SDL 2.

Base: edgar_1.38.orig.tar.gz from Debian (sha256
23e57debc5e6995447bba3b64513e420e111ce24644a3a303237f4379ba3e710).
Branch team2/edgar-amiga.

Status: builds; not yet run in the lab.


What you need
-------------

- A 68040 or 68060 with an FPU, AmigaOS 3.x, an RTG card (or the
  AmigaChrome lab).
- GFOpenUp 0.8.18 or later: LIBS:OpenGPU/SDL2.module, SDL2_image.module,
  SDL2_mixer.module and SDL2_ttf.module.
- About 230 MB of disk (the music alone is 77 MB of Ogg Vorbis).


How to play
-----------

Open the Edgar icon, or run Edgar from a Shell. The game reads its data
from its drawer and keeps its settings and saved games there too.


Building
--------

    make -f amiga/Makefile.amigaos -j2 dist

with GFOpenAmigaGCC 16.2.0-open4, the OpenNDK headers, the OpenGPU kit and
the Team's static libpng and zlib (see the Makefile's head). The drawer is
dist/Edgar (and dist/Edgar.info).


What was changed
----------------

- src/main.c: main() first moves into the drawer (amiga/amiga_start.c), and
  closes at exit the screens SDL2.module 0.6 can leave
  (amiga/amiga_screens.c). amiga/stack.c: 1 MB of stack.
- amiga/Makefile.amigaos: upstream's makefile's objects (amiga/sources.mk)
  with its non-Unix settings (UNIX=0: saves in the current drawer) and no
  pak file (the data unpacked in the drawer).
- The drawer's 8-bit RGB PNGs are stored as RGBA (amiga/tools/png_rgba.py,
  as in the Blob Wars port: SDL2_image.module mis-decodes some of them).
- No translations yet: the game is in English (upstream's .po files are
  not compiled into .mo files here).


Licences
--------

The Legend of Edgar: GPL 2 or later (COPYING.txt; the game's graphics
too). Its music and sounds: CC BY 3.0, CC BY-SA 3.0, CC0 and others, file by
file in doc/ (upstream's doc/music_and_sound_licences, in the drawer).
The Amiga files (amiga/): GPL 2 or later, the AmiCradle Team.
