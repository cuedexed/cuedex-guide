# What's new in CueDex

The newest version comes first. See [the guide](GUIDE.md) for how each feature works.

## 0.6.0

### Shared cues

- Cue layers per track: MY, SHARED (pinned to a version and aligned to your copy), FORK, MERGED, AUTO and a frozen,
  hash-pinned SHOW copy, each cue with its origin. Downloaded cues stay rehearse-only until you arm them. Show mode
  plays every track's SHOW layer and nothing else. See [Layers and shared cues](GUIDE.md#layers-and-shared-cues).
- Library → Shared: search by text, ISRC or this copy's fingerprint, preview a shared set as a layer, review updates
  change by change, vote and flag, and publish your own set (signed with a key kept in your keychain, CC0, with a short
  proof of work instead of an account).
- Shared cues are aligned to your copy of the music by fingerprint and refined on your own audio (0.011 ms at the
  99th percentile).
- The public cue repository on GitHub is CueDex's default source, and an offline bundle of it can be downloaded and
  verified for venues without a network. See [Sharing cues](CONTRIBUTING.md).

### Steady numbers

- Nothing moves when a number changes. Every time counter, rate, meter reading, badge and status line sits in
  a fixed space, in the main window, the Show window and the web remote. A test drives every view through running
  clocks, rates, seeks and counters in every font and text size and fails if any widget moves at all.
- Every bundled font now has fixed-width digits.
- The Show window keeps GO, the transport buttons and PANIC on screen at every window size.
- The timeline no longer blanks for one frame when it follows the music to the next track.
- Labels and tooltips no longer use internal test names.
- Rehearse says what it does: **REHEARSE: cues off** / **LIVE: cues on** (timecode keeps running in rehearse).
- The paused symbol and other symbols show in every font (some fonts had no glyph for them).
- The light theme: the time counter, GO / PANIC and the lane headers are readable.
- The listener's level meter starts at silence (it showed a full-scale 0.0 dBFS before anything was heard).

### The guide

New: the user guide, the TL;DR and this page.

## 0.5.5

- The listener's precision no longer depends on when its capture started: under 1.6 ms at the 99th percentile on clean audio.
- **Honour lane leads at GO**: a cue at the GO position on a lane with a lead goes out on time; the music waits that lead.
- OnTheWire direct publishes a GO the moment it happens, with its exact start time.

## 0.5.4

- Instant GO for CueDex's own player: the audio callback starts music and LTC together on its next buffer. From key
  press to sound: 8.3 ms median.
- **GO starts**: **Instant — in the next audio callback**, **Readable first frame — + one LTC frame of pre-roll** or
  **Look-ahead**.
- **IO buffer** per device (default 64 frames).
- Fixed: a gapless advance could be missed when the Mac was busy or the window hidden.
- The transport buttons stay at a fixed distance from the time counter.

## 0.5.3

- Cued GO with Hybrid start is the default on Music and the Spotify app.
- Playlist, album and set links: listed first, then fetched in order, with a download archive. **New Set from Link…**
  makes a new set from a link.
- The **CUED** badge: CueDex's own player has the GO position decoded and ready.
- <kbd>Space</kbd> is always play / pause, even when a button has focus.

## 0.5.2

- Cued GO (pre-cue): the track is loaded and placed, paused and silent, before the GO; the GO is a resume.
- TIDAL as a route (Now Playing and MediaRemote); in the app a TIDAL track is followed through Now Playing.
- Hybrid starts with one LTC frame of pre-roll, so the first readable frame comes with the sound.
- Fixed: running the tests could clear the Spotify Client ID in the preferences.

## 0.5.1

- The listener relocks after a hot cue or a loop exit in about 1.3 s (was 2.8 s), handles crossfades and repeated
  sections, and reports Lost on digital silence within about 0.6 s.
- Hybrid start mode, Spotify's seek offset compensated, per-track start offsets.

## 0.5.0

- External tracks: CueDex starts Spotify (desktop app or Web API) or Music and starts its timeline on the player's
  first sound; it follows the player's own play, seek, pause and track changes, and follows any Now Playing app.
- Paste a link: tracks fetched with `yt-dlp` become normal file tracks CueDex plays itself.

## 0.4.0

- The listener: follow music CueDex does not play, from the whole Mac, one app or an input, by fingerprint; LTC, MTC,
  Art-Net and cues follow what is heard.

## 0.3.0

- The CueDex app: the set view, the timeline with lanes over the waveform, every cue editor, devices and calibration
  cards, the pre-show check, OnTheWire direct, the Show window and the iPad / iPhone web remote, with the engine inside
  and live cue edits while playing.
- The cue engine: OSC (with target profiles for Resolume Arena, QLab, grandMA3, ChamSys MagicQ and Bitfocus Companion),
  MIDI, MIDI clock and MIDI Show Control, sent at the exact instant the music reaches them.
- CueDex's own player: music and LTC in one audio callback, one timecode hour per track, gapless track changes.
- Timecode out: LTC, MTC and ArtTimeCode from one transport.
