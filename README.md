# Torchlight Recompiled

Native PC port of the Xbox 360 (XBLA) version of Torchlight. **No game files are included**: you need your own copy.

**Download:** see [Releases](../../releases).

## WHY I MADE THIS

The original PC Torchlight (2009) has no real controller support. It is built
around the mouse cursor, and mapping a gamepad to the mouse with tools like
Xpadder feels awful.

The 2011 Xbox 360 version is the one Runic Games designed for a controller, but
until now it only ran on a 360 or in an emulator. I wanted the best of both:
the console version's controls, running natively on PC with better graphics,
high resolutions and high frame rates.

## HOW THE XBOX 360 VERSION DIFFERS FROM THE ORIGINAL PC VERSION

What Runic changed for the 360 version, according to their own notes before
launch:

  - The UI was redesigned from the ground up for a TV and a gamepad
  - You move your character directly with the stick, with analog movement
    speed and no virtual cursor
  - Auto-targeting for ranged attacks; the trigger controls how far lobbed
    skills go
  - Melee was reworked to hit everything in front of you, with new attack
    animations
  - 8 mapped skills (4, plus a second set you swap with the D-pad)
  - No inventory grid: you carry 50 items, potions and scrolls stack to 99,
    and the game picks the best potion for you
  - Rumble for quakes, hits, low health and fishing
  - Features brought back from Torchlight 2's development: a new pet, a new
    armor set for each class, random quests from a miner in town, the newer
    automap, smoother animation blending and shorter loading
  - Everything else from the PC version is still there: socketing,
    enchanting, fishing, transmuting and the endless dungeon

Sources:
  https://www.engadget.com/2011-01-06-runic-details-how-torchlight-will-be-different-on-xbla.html
  https://gamebanshee.com/dxcd
  https://gog.com/forum/torchlight_series/is_this_game_playable_with_a_pc_controller/page1

## WHAT THIS PORT ADDS ON TOP OF THE XBOX 360 VERSION

Graphics and performance
  - True render resolution up to 4K (1080p, 1440p, 4K, Auto or your own
    scale). The 3D scene and menus are drawn at that size, not stretched
  - Up to 120 fps (or unlimited); game speed stays correct at any frame rate.
    Holds a steady 120 fps at 4K
  - FXAA anti-aliasing, up to "FXAA Extreme"
  - Colours and gamma match the original console look
  - Windowed, borderless fullscreen (default) or exclusive fullscreen with your
    choice of refresh rate
  - V-Sync on/off
  - Every 2D image of the interface (menus, icons, loading screens, logos)
    AI-upscaled 4x on your PC at the first start, with sharp high-res fonts
  - Faster loading screens, and a loading hourglass that no longer flickers

PC polish
  - Settings.exe: a settings window with every graphics option, the save
    location and a Play button
  - In-game PC Settings menu (Options -> PC Settings, or the PS button), with
    the same options, applied instantly
  - No config files to edit: settings are saved automatically in an encoded
    file
  - Button prompts follow your controller: PlayStation buttons and a PS4-style
    controller diagram on a DualSense / DualShock, Xbox buttons on an Xbox pad.
    All Xbox LIVE wording has been removed
  - The "press Begin" controller screen is skipped: the game starts on the
    title menu, after the startup logo (3 seconds) and a smooth fade-in
  - On-screen keyboard for naming your hero and pet, with a Cancel button
  - Local achievements with their original icons
  - Fixed audio crackling caused by sound buffer underruns
  - All game data is packed into a single encrypted file (Torchlight.pak),
    so the folder stays clean

Under the hood
  - Built with XenonRecomp / XenonAnalyse (PowerPC code) and XenosRecomp
    (shaders), with a runtime based on UnleashedRecomp
  - 61,973 PowerPC functions translated to C++ and compiled into a native
    x64 exe
  - Xenos GPU shaders converted to SPIR-V and rendered with Vulkan; window,
    sound and controllers through SDL2
  - Much lower CPU and GPU use than running the game in an emulator

## FIRST START: ADD YOUR OWN GAME

This folder does not include the game. You need your own copy of Torchlight
for Xbox 360 (Xbox Live Arcade, title ID 58410A7E).

  1. Put your game into the "game" folder. That can be:
       - the game package from your console's hard drive or from Xenia's
         content folder (the folder named 58410A7E, or the file inside it), or
       - an already unpacked game folder (with default.xex and pak.zip).
     Xbox Live Arcade games come as a package, not as an ISO.
  2. Start Settings.exe or TorchlightRecomp.exe and press Continue.
  3. The app checks that it is the exact version this build was made from,
     unpacks it, makes the sharp AI-upscaled menus and icons on your graphics
     card, and packs everything into Torchlight.pak. This takes a minute or two.
  4. Done: from now on it starts like a normal PC game. The files in the "game" folder
     are not needed any more; you can delete them.

To give the folder to someone else later, open Settings.exe and press
"Reset to Shareable": it removes the game data, the saves and the game copy.

## WHAT'S IN THIS FOLDER

  TorchlightRecomp.exe   The game. Double-click to play.
  Settings.exe           Settings window (graphics, save location, Play).
  dxcompiler.dll         Shader compiler used by the game.
  game\                  Put your own copy of the game here (first start only).
  Torchlight.pak         Made on the first start from your copy: the game data,
                         packed and encrypted.
  UserData\              Created the first time you play: your saves,
                         settings, logs and caches.
  README.txt             This file.

## HOW TO PLAY

  1. Plug in a controller (DualSense, DualShock 4, Xbox or any controller
     Windows recognises).
  2. Double-click TorchlightRecomp.exe, or open Settings.exe and click Play.
  3. The game starts in borderless fullscreen. Alt+Enter switches between
     windowed and fullscreen.

Controls are the original Xbox 360 controls. The button pictures follow your
controller: Xbox buttons on an Xbox pad, PlayStation buttons on any other.
The game is controller only: the mouse and keyboard are not used in game.

Settings
  - Before playing: open Settings.exe. It works with the mouse, the keyboard
    or a controller, and every change is saved as you make it.
  - While playing: Options -> PC Settings, or press the PS / Guide button.

Requirements
  - Windows 10 or 11, 64-bit
  - A CPU with AVX (any Intel or AMD CPU from about 2011 onwards)
  - A graphics card with Vulkan support

## SAVES

Your saves, settings, logs and caches are kept in one place. You choose where
in Settings.exe -> Save Location:

  Game Folder (default)   <this folder>\UserData
  Documents               Documents\My Games\Torchlight Recompiled
  AppData                 %LOCALAPPDATA%\Torchlight Recompiled

Changing the location moves everything there, so there are never two copies.
"Open Save Folder" in Settings.exe opens the current one.

To start completely fresh, delete the UserData folder (or whichever folder you
chose). If the game folder can't be written to (for example inside Program
Files), the game uses AppData automatically.

## KNOWN LIMITS

  - Controller only. Mouse and keyboard play was tried and removed because it
    wasn't solid enough.
  - Xbox LIVE features (leaderboards, online) are not available. Achievements
    are kept locally.

## WHAT'S NEXT

  - A native Android (ARM64) version.

## LEGAL

This is a fan project, not affiliated with or endorsed by Runic Games, Perfect
World or Microsoft. Torchlight and its content belong to their owners.

This folder contains no game files, art, music or sound. You need your own
legally obtained copy of the Xbox 360 version of Torchlight.

The AI upscaling uses Real-ESRGAN (realesrgan-ncnn-vulkan and the
realesrgan-x4plus-anime model, BSD 3-Clause licence, by Xintao Wang et al.),
carried inside TorchlightRecomp.exe and run once on the first start.

XBOX 360 Recomp by r/evillurkz
