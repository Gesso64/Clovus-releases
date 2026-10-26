# Clovus

A free Windows soundboard with an **instant-replay buffer**. Press a hotkey and Clovus saves the last 10 to 180 seconds of
one app's audio (normally Discord, so you capture your friends' voices) as a clip. Trim it, change its tone and loudness,
give it a hotkey, and play it back into voice chat like any other sound.

**[Download the latest version](../../releases/latest)** (a zip with `clovus_app.exe`; no installer, just unzip and run).

This page is for downloads only. The source code is not published; Clovus is free to use but not open source (see
[LICENSE.txt](LICENSE.txt)).

## What it does

- **Soundboard.** Tabs are real folders under your clips folder (default `Music\Clovus`). Add or drop WAV, MP3 and FLAC files,
  give each a global hotkey, volume and play mode (restart, overlap, toggle or loop). Select several clips at once to move them.
- **Replay buffer.** Records one app (or everything except Clovus) and saves the last 10 to 180 seconds with a hotkey, into an
  `Inbox` tab. Off by default.
- **Clip editor.** Trim, speed and pitch, tone (EQ), compressor, mono and pan, gain, fades and echo, all non-destructive with
  undo. Preview every clip on your headphones only, never to the chat.
- **Looks.** Five colour themes, any accent colour, and an interface size from 75% to 200%.

## Requirements

- Windows 10 version 2004 (build 19041) or newer, or Windows 11.
- Nothing else is needed to use the soundboard and the editor: clips play on your speakers or headphones out of the box.
- **Optional:** to play clips *into a voice chat* (so your friends hear them), you need a virtual audio device that the chat app
  can use as its microphone, such as [VB-Cable](https://vb-audio.com/Cable/) or [Voicemeeter](https://vb-audio.com/Voicemeeter/).
  Clovus does not install or include one. If you already route audio some other way (for example a mixer or a second sound card),
  just pick that device as the chat output; no virtual device is required.

## Getting sound into Discord (optional)

Clovus plays each clip on two outputs: the **Chat output** (what your friends hear) and the **Monitor device** (what you hear).
Discord listens to one input device, so the chat output has to reach it. If you only want to hear clips yourself, leave the
chat output unset and skip this section.

1. Install VB-Cable (or use any other virtual or physical route into your chat app).
2. In Clovus, set *Chat output* to `CABLE Input`.
3. In Discord, set *Input device* to `CABLE Output`.

That replaces your microphone in Discord. To keep talking, mix your microphone into the cable (Windows "Listen to this device"
on the microphone, playing through `CABLE Input`) or use Voicemeeter: set *Chat output* to `VoiceMeeter Aux Input`, route your
microphone and the Aux input to the virtual output Discord listens to, and pick the matching device in Discord.

In Discord, turn off Krisp noise suppression, automatic gain control, echo cancellation and the automatic input-sensitivity
gate for that input, or effects get mangled and clip starts are cut. The first-run wizard and the **Checks** page in
Settings look at your devices and tell you what is missing or likely mis-routed.

## Notes

- **Windows may warn on first run.** The program is not code-signed, so SmartScreen may say "Windows protected your PC". Choose
  *More info*, then *Run anyway*. Some antivirus tools are wary of any program that registers hotkeys and reads audio sessions.
- **Recording other people.** The replay buffer can capture other people's voices. In many places saving or sharing someone's
  voice needs their consent, so tell the people in your call before you use it. The buffer lives in memory only, records
  nothing until you switch it on, and writes a file only when you press a save hotkey.
- **Hotkeys** are global (`RegisterHotKey`): Clovus takes those keys system-wide while it runs. Modifier combinations and F13 to
  F24 are the safe choices.
- **Where files live:** settings in `%APPDATA%\Clovus\config.json`, log in `%APPDATA%\Clovus\clovus.log`, clips in your clips
  folder. Closing the window hides Clovus to the tray so hotkeys keep working; quit from the tray menu.
- **Command line** (also what a Stream Deck button can call): `clovus_app.exe --show`, `--save N` (replay slot 1 to 3),
  `--stop-all`, `--quit`, `--minimized`.

## Feedback

Found a bug or have an idea? Open an [issue](../../issues) on this page and include what you did, what you expected, and the
log file if you can (`%APPDATA%\Clovus\clovus.log`).

Clovus is copyright (c) 2026 Gesso64. Third-party components and their licences are listed in
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
