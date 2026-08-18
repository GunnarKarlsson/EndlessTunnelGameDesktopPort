# EndlessTunnelDesktop

Port of the open source Android NDK game [Endless Tunnel](https://github.com/googlesamples/android-ndk/tree/master/endless-tunnel) to desktop using Qt. Uses OpenGL 2.0 as per the source project. Covers the welcome and gameplay scenes.

Original Android project code: https://github.com/googlesamples/android-ndk/tree/master/endless-tunnel

## License

This desktop port is released under the [MIT License](LICENSE).

That license does **not** cover the original Android Endless Tunnel source code. Those files remain copyright Google Inc. and are licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0). See the original project and the Apache license headers in those source files.

## Building

This is a Qt Widgets / OpenGL application (`EndlessTunnelPort.pro`). It needs:

- **Qt 5** (Core, Gui, Widgets) with a C++ compiler
- **[GLM](https://github.com/g-truc/glm)** (header-only math library)
- An OpenGL 2.1 capable GPU/driver (the window requests OpenGL 2.1)

1. Install Qt 5 (Qt Creator is optional but convenient).
2. Get GLM. Then edit `EndlessTunnelPort.pro` and set `INCLUDEPATH` to the directory that contains the `glm/` folder, for example:

   ```
   INCLUDEPATH += /path/to/glm
   ```

   On macOS with Homebrew, that path is often `/opt/homebrew/include` or `/usr/local/include`.

3. Build with qmake:

   ```
   qmake EndlessTunnelPort.pro
   make
   ```

   Or open `EndlessTunnelPort.pro` in Qt Creator, choose a Desktop kit, and build.

## Running

After a successful build, run the `EndlessTunnelPort` binary from the build directory.

- **macOS:** `open EndlessTunnelPort.app`, or run `EndlessTunnelPort.app/Contents/MacOS/EndlessTunnelPort`
- **Linux:** `./EndlessTunnelPort`
- **Windows:** `EndlessTunnelPort.exe`

From Qt Creator, use Run.

The game window is 800×600 by default.

## How to Play

You are a ship flying down an endless tunnel. Obstacles appear as colored blocks in a 5×5 grid; fly through the gaps and collect the small shimmering white cubes.

**Start:** On the title screen, click **Play!** (or click anywhere) to begin.

**Steer:** Use **WASD** or the **arrow keys**. The ship moves forward on its own; you only control left/right/up/down. At higher levels the tunnel can roll, so “up” follows the view.

**Score and lives:**

- Collect a white bonus cube for **+50** points.
- You start with **4 lives** (hearts in the top right). Score is in the top left.
- Hitting a colored block costs a life (`Ouch`) and knocks you back. Lose all lives and it is **Game Over**; you return to the title screen.

**Levels:** Every **500** points the difficulty goes up: you fly faster, and obstacles get harder.

## To do

+ Add the about and story sections.
+ Update shaders to OpenGL 330 or higher

![Screen shots](https://github.com/GunnarKarlsson/EndlessTunnelDesktop/raw/master/screenshot.png)
