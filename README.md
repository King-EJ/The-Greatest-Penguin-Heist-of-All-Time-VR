# The-Greatest-Penguin-Heist-of-All-Time-VR
VR Mod for The Greatest Penguin Heist of All Time

PENGUIN HEIST VR  v0.3.3
"The Greatest Penguin Heist of All Time" (Unity 6000.4, Mono x64)
==========================================================================

NEW IN 0.3.3
* How long to hold: [Bindings] YHoldSeconds (default 0.6) and XHoldSeconds (default 0.4).

NEW IN 0.3.2
* Hold Y (0.6 s) = gun adjust mode on / off. Tap Y = Y as before. (Y + left stick click is still the
  VR settings menu.)  [Bindings] YHold = GunAdjust
* Hold A + click the left stick = Back (gamepad View/Select).

NEW IN 0.3.1
* Gun adjust: now saved for EACH gun separately (BepInEx\config\PenguinHeistVR_guns.txt).
  Start / stop: HOLD Y (or "Adjust gun position" in the VR settings menu).
    Hold left grip ........... grab the gun with your left hand and move / turn it where you want it
    Left stick ............... fine move (+ left trigger: forward/back)
    Right stick up/down ...... gun size        Right stick left/right ... roll
    B = reset this gun         A = done (saved)
  Both stick clicks are only re-centre again.
* Hand HUD: health and objectives float by your left hand, the ammo next to your gun, and they are
  left out of the big screen. Paused / menus: back on the big screen. [UI] HandHud / HandHudSize, also
  in the VR settings menu.
* Head hiding: the penguin is one mesh, so 0.3.0 only hid the name tag. Now the head's part of the
  mesh is shrunk away in first person (the log says which bone: "head bone ...").

NEW IN 0.3.0
* Gun adjust mode: HOLD both stick clicks (1.2 s) - or "Adjust gun position" in the VR settings menu.
    Left stick ............... move the gun right/left, up/down
    Left stick + left trigger  move it forward/back
    Right stick .............. turn it left/right, tilt it up/down
    Right stick + right trigger roll
    B = reset to 0      A (or hold both sticks again) = done, saved to the config
  The values are shown on the screen. A short click of both sticks still re-centres.
* Hold Y = Back (gamepad View/Select). Tap Y = Y as before. [Bindings] YHold (None = off).
* First person: your own penguin's head is hidden (it got in your view when walking) - it still casts
  its shadow. [Camera] HideHeadInFirstPerson, also in the VR settings menu. The head smoothing from
  0.2.9 no longer trails behind by more than 3 cm.

NEW IN 0.2.9
* Found why the menus vanish when you go back to the main menu: the game's graphics settings set the
  view distance of EVERY camera when the main menu loads, including the mod's UI camera - the menus
  ended up beyond its view distance. The UI camera's settings are now held every frame.
* First person: the penguin's head bobs at the physics rate, which shook the view. The head position
  is smoothed now (up/down more than sideways). [Camera] EyeSmoothing (0 = off, 1 = normal, 2 = more),
  also "Head smoothing" in the VR settings menu.
* Main menu shaking = low frame rate there (35-48 fps, the menu scene is heavy). [General] RenderScale
  = 0.7 helps a lot.

NEW IN 0.2.8
* Menus: the UI picture sometimes stops drawing (it happened when you went back to the main menu).
  The mod now keeps watching it the whole game: if menu parts should show but the picture is empty,
  it re-attaches the menus to the UI camera, and if that does not help, switches the camera set-up.
  Starts with the set-up that worked for you (perspective).
* Pause menu: the game turns on a depth-of-field blur when you pause - that made the whole world
  fuzzy. Switched off ([Camera] NoDepthOfField, also motion blur: NoMotionBlur; both in the VR
  settings menu).

NEW IN 0.2.7
* 0.2.6 put the menu buttons in the right places (the log confirms Play / Shop / Options / Exit are
  now on the picture), but the UI camera then drew nothing at all. The mod now checks the picture
  itself: if menu parts should be visible but the picture stays empty, it switches to another UI
  camera set-up (3 in turn) and keeps the first one that shows the menus. The log says which one
  ("UI set-up in use: ..."). This takes a few seconds on the main menu.

NEW IN 0.2.6
* Menus (main menu, lobby, shop, pause): the game shows / hides its menu pages by moving them to
  positions worked out for the flat screen. The VR screen now uses exactly the flat screen's layout
  (same size as your game window), so the pages land where they should.
* Right stick click = d-pad up (was d-pad down). Hold X = d-pad down, tap X = X as before.
  [Bindings] RightStickClick / XHold (XHold = None turns the hold off).

NEW IN 0.2.5
* Menus: the pictures you sent showed the money counter and title fine but no buttons. The log showed
  why: the game's buttons (Play / Shop / Options / Exit, the lobby's Plan Heist / Shops / Leave, the
  shop buttons) sit at a different depth than the rest of their menu. The flat game ignores that, the
  VR screen's camera did not. The VR screen now draws flat (orthographic), so depth no longer matters.
* The debug pictures are still saved (BepInEx\PenguinVR_UI_*.png); turn off with
  [Debug] SavePictures = false once the menus work.

NEW IN 0.2.4
* VR settings menu: hold Y + left stick click for 1.7 s (same as Wobbly Life / Patrick VR).
  Right stick up/down = choose, left/right = change, A or right trigger = toggle, B = close.
  The game gets no input while it is open. Changes are saved straight away.
* Flippers follow your hands in first person (like Wobbly Life VR). Settings menu or
  [Arms] ArmsFollowHands / ArmsInThirdPerson (off by default) / ArmsWeight.
* Menus still missing: the mod now saves pictures of what it draws, so I can see what goes wrong:
    BepInEx\PenguinVR_UI_Main_Menu.png     (what the floating UI screen holds)
    BepInEx\PenguinVR_View_Main_Menu.png   (what your left eye sees)
  and the same with the level's name once you are in a game. PLEASE SEND THESE PNGs with the log.
  Turn off afterwards: settings menu "Save debug pictures" or [Debug] SavePictures = false.
* Tip: if you can see the VR settings menu but not the game's menus, the floating screen works and
  the problem is the game's menus; if you can't see the settings menu either, the screen itself is
  not showing - please tell me which.

NEW IN 0.2.3
* Menus: the UI screen was see-through but empty. The last log showed the menu buttons are there but
  the picture behind them came out solid black, covering them. The UI picture now only draws the menu
  layer, and the game's sky / fog / weather effects are switched off while it draws.
* Shaking: the log shows 36-50 fps while the headset wants 72. Below 72 the headset fills in the
  missing frames, and that judders. To get closer to 72, in BepInEx\config\eavincentj.penguinheist.vr.cfg:
    [General] RenderScale = 0.7      (try 0.6 if still low)
    [Camera]  PostProcessing = false
  The log prints "Frame rate N fps" every 10 s so you can see the difference.

NEW IN 0.2.2
* Menus: the view no longer shakes. The main menu's camera sways; the VR view now holds still and
  only moves when the menu camera really moves (more than 1.5 m or 35 degrees).
* Menus: if the floating screen comes out solid black, it switches to see-through drawing so the
  buttons show. The log now says what the screen's picture looks like ("UI picture: ...") and what
  each menu screen contains ("UI canvas ... :"), plus the frame rate ("Frame rate N fps").
  Please send the log after a test.

NEW IN 0.2.1
* Fixed: no menus / HUD in VR. The game's 2D screens are now drawn into a floating screen in front of you
  (always on top of the world). The log lists every menu screen it puts there ("UI canvas on the VR screen").

INSTALL
1. Copy everything in this zip into the game folder (next to Penguin Heist.exe).
   You get winhttp.dll, doorstop_config.ini, .doorstop_version and the BepInEx folder
   (BepInEx 5.4.23.5 + the VR mod).
3. Start SteamVR / Quest Link / Virtual Desktop first (it must be the OpenXR runtime).
4. Start the game. The first start takes a little longer (BepInEx sets itself up).
   If the headset stays black, add the Steam launch option  -force-d3d11

WHY BEPINEX 5.4.23.5
BepInEx 5.4.23.2 (the version in v0.1.0 and in the Wobbly Life zip) uses Doorstop 4.3.0,
which crashes this Unity 6000.4 game at start-up. 5.4.23.5 has Doorstop 4.5.0 and a Unity 6 fix.

HOW IT PLAYS
- First person from your penguin's head (hats hidden). Walking goes where you look.
- Your gun follows your right controller and shoots where it points.
- Third person (F9 or [Camera] FirstPerson = false): you stand where the game's camera is.
- Menus and HUD: on a floating screen in front of you.

CONTROLS (the VR controllers act as an Xbox controller for the game)

  Left stick ........ walk                    Right stick L/R ... snap turn
  
  Right stick up .... next weapon             Right stick down .. previous weapon
  
  Right stick click . d-pad up                 Left stick click .. slide
  
  Right trigger ..... use / fire (also aims with a gun)
  
  Left trigger ...... aim
  
  A / B ............. jump / reload           X / Y ............. interact / penguin sense   (hold X = d-pad down, hold A + L3 = Back)
  
  X + Y together .... pause                   Grips ............. left / right punch
  
  Both stick clicks . recenter (keyboard F8)  Hold Y = gun adjust  F9 / F10 .......... first-third person / gun in hand
  
Change any of these in BepInEx\config\eavincentj.penguinheist.vr.cfg, section [Bindings].


Credits: OpenXR.dll bridge by Astien (see BepInEx\plugins\PenguinHeistVR\LICENSES),
BepInEx 5.4.23.5 (LGPL-2.1).
