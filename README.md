## Features

- Continuously checks multiple international earthquake networks.
- Displays M2.5+ events in a worldwide real-time event list.
- Animates the map to the epicenter when new or revised information arrives.
- Shows a one-minute preliminary-information panel with location, magnitude, depth, date and time, and source.
- Supports worldwide ADM0 boundaries and local ADM1–ADM3 boundaries where available.
- Draws USGS ShakeMap intensity contours when official contour data is available.
- Handles longitude wrapping for events near Alaska and the International Date Line.
- Provides M2.5+, M4.5+, and M6+ event filters.
- Includes native Windows magnitude-alert playback suitable for normal speakers or a virtual audio cable.
- Supports Windows TTS, Azure Speech, ElevenLabs, and Gemini TTS.

## Earthquake sources

| Source | Region or role | Announcement language |
|---|---|---|
| USGS | Worldwide | English |
| EMSC | Worldwide | English |
| GEOFON | Worldwide | English |
| EARLY-EST | Rapid earthquake and tsunami estimation | English |
| CENC | China | Chinese |
| BMKG | Indonesia | Malay |
| SSN | Mexico | Spanish |
| FUNVISIS | Venezuela | Spanish |
| INGV | Italy | Italian |

Availability depends on each provider's network, feed format, and uptime. All earthquake information remains preliminary until reviewed by the reporting agency.

## Install on Windows

1. Download **WEQ-DP Realtime Earthquake alpha 2.2 Setup.exe** from the latest GitHub release.
2. Open the installer and choose an installation folder.
3. Optionally create a desktop shortcut.
4. Select **Run WEQ-DP Realtime Earthquake** when installation finishes.

The installer uses a per-user location by default and does not require administrator privileges:

```text
%LOCALAPPDATA%\WEQ-DP Realtime Earthquake
```

Windows 10 or Windows 11 is recommended. The application uses Microsoft Edge WebView2 for its interface.

## Magnitude audio

Alpha 2.2 includes three custom WAV alerts:

| Magnitude | File |
|---|---|
| M2.5–4.9 | `magnitude-2.5-4.9.wav` |
| M5.0–6.9 | `magnitude-5.0-6.9.wav` |
| M7.0–9.9 | `magnitude-7.0-9.9.wav` |

For each new or revised earthquake, WEQ-DP follows this order:

1. Play the matching magnitude WAV completely.
2. Speak the multilingual TTS announcement.

Installed audio files are located in:

```text
%LOCALAPPDATA%\WEQ-DP Realtime Earthquake\audio
```

Files must be valid WAV audio and no larger than 20 MB each. If a custom file is missing or cannot be played, the app uses a generated fallback cue.

## Text-to-speech

Open **Menu** and select a speech engine:

- **Azure Speech** — enter the Speech resource key, region, and the five voice selections.
- **ElevenLabs** — enter an API key and separate voice IDs for each language.
- **Gemini voices** — enter the required API key and select the available voices.
- **Windows TTS** — used as the local fallback when a cloud engine is unavailable.

Cloud speech can be configured separately for English, Chinese, Malay, Spanish, and Italian. Enabling a cloud speech engine automatically enables Voice Alerts. API keys remain in memory for the current session and are not written to disk.

## OBS Studio audio routing

WEQ-DP plays magnitude alerts through the Windows default output device. For dedicated OBS routing:

1. Install or select a virtual audio cable.
2. Set the cable as the Windows output device used by WEQ-DP.
3. Add the cable's recording endpoint to OBS as an **Audio Input Capture** source.
4. Test each alert from **Menu → Magnitude audio**.

## Build from source

Requirements:

- Windows 10 or 11
- Go 1.25 or newer
- Wails 2.15
- NSIS 3.12 or newer for the installer

Data and map attribution

- Earthquake data is supplied by the agencies listed above and may be revised without notice.
- Administrative boundaries use geoBoundaries/geoBoundaries CGAZ data where available.
- ShakeMap products are retrieved from USGS when the selected event provides them.
- Agency names and trademarks belong to their respective owners.

## Reporting problems

When opening a GitHub issue, include:

- WEQ-DP version
- Windows version
- Earthquake source involved
- Whether the problem affects the map, audio, or TTS
- A screenshot and the approximate event time

Do not include Azure, ElevenLabs, Gemini, or other private API keys in screenshots or issue reports.
