Graphical Mixer Interface for the Scarlett series
=================================================

Currently supported models, first generation of
- 18i6
- 18i8
- 18i20
- 6i6 (untested)

third generation of
- 8i6

This is just a GUI, the device **must** be supported by the ALSA Linux kernel device-driver.

The mixer-elements are numerically indexed and only work with vanilla Linux.
All 1st generation of Scarlett devices are supported (Linux 4.16, April 2018), 3rd generation 8i6 devices are supported and some other 2nd and 3rd generation devices may happen to work.

This UI a **quick hack**, it may or may not work and is prepared for other Scarlett devices, but **you** **are** **on** **your** **own**.

Please do **not** package this software as-is, nor make it available to end-users since most will be disappointed.

Setup
-----

Build-dependencies: gnu-make, a c-compiler, pkg-config, libpango, libcairo,
lv2 (SDK), alsa (libasound) and openGL (sometimes called: glu, glx, mesa).

```bash
  git clone git://github.com/x42/scarlett-mixer
  cd scarlett-mixer
  git submodule init
  git submodule update
  make
```

Usage (run from source-dir)
---------------------------

```bash
  ./scarlett-mixer --help
  ./scarlett-mixer hw:2   # change "hw:2" to match your device
```

Screenshot
----------

![screenshot](https://raw.github.com/x42/scarlett-mixer/master/scarlett-mixer-gui.png "Scarlett 18i6 Mixer")

See also
--------

ALSA Mixer in HTLM-5 with ALSA JSON Gateway: https://github.com/fulup-bzh/AlsaJsonGateway


-------------------------------------- %< snip, snip >% ---------------------------------------

My Scarlett Gen 3 8i6 Changes:

This is my first git-hub commit so be forewarned.

Tested on 3rd Gen Scarlett 8i6 on Debian 11, kernel 5.14.9 against beta alsamixer in kernel 5.14.

- Fixed negative and off-by-1 index problems that were truncating labels.
- Fixed AIR and PAD widget updates that were not responding to external changes.
- Moved Hiz, Pad, Air button stack up 2 rows.
- Added Clock Source widget (Internal/SPDIF).
- Added Clock Sync Source display widget (Locked/Unlocked)
- Added Phantom Power widget.
- Added Phantom Power Persist widget.
- Added ability to rapidly scroll through long lists of selector items "transparent scrollbar".
  Just click the selector widget with mouse button 1, drag left or right until desired selection 
  is displayed and then release button 1.  
  Leaving the widget's real-estate will also terminate the selection leaving the last displayed 
  selection as the current.  This is VERY FAST compared to 10 or 20 mouse clicks.

Files Changed:

- scarlett_mixer.c - Index fixes, additional widgets, etc.
- robtk_selector.h - Added "trasparant scrollbar" functionality to selector list widgets
- robtk_checkbutton.h - Added robtk_cbtn_set_active_text(..., bool v, char *on, char *off) helper function

Notes:
- robtk_selector.h and robtk_checkbutton.h will have to be placed in their appropriate directories.

Original:
![screenshot](https://github.com/92es/scarlett-mixer/blob/master/Scarlett%208i6%20Mixer%20Before.png "Original Scarlett 8i6 Mixer")

Updated:
![screenshot](https://github.com/92es/scarlett-mixer/blob/master/Scarlett%208i6%20Gen%203%20Mixer%20After.png "Modified Scarlett 8i6 3rd Gen Mixer")
