# Scripture AI (web app, stage 1)

Listens to the preacher, finds the scripture being mentioned, and puts it on screen.
Works as a normal website and installs like an app (PWA). After the first visit it opens with no internet.

## Put it online with GitHub Pages (free)
1. Create a GitHub repository and upload every file in this folder (index.html, scripture.js, kjv.json, sw.js, manifest.json, icon.svg).
2. Repository Settings, Pages, Source: "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
3. Open the address GitHub shows (https://YOUR-NAME.github.io/REPO/). Use Chrome or Edge.
4. Click the install icon in the address bar to install it on the PC.

To try it on your own PC first: `python -m http.server 8000` inside this folder, then open http://localhost:8000.
Double-clicking index.html does NOT work (browsers block loading kjv.json from a file).

## Using it in a service
- Start listening, allow the microphone.
- Say or type "turn to John 3:16", or quote a verse. High-confidence matches go on screen automatically; others wait as a suggestion with a Show button.
- Open output window: send it to the projector (drag to that screen, press F11). In vMix/OBS use Window Capture on it. Pick the Green background and chroma key it, or Transparent.
- Keys: Right arrow = next verse, Left arrow = previous, B = blank screen.

## Honest limits of this version
- Speech: the browser's speech recognition (Chrome/Edge) sends audio to Google, so it needs internet. With no internet the app still opens, you can search and show verses by hand, and typing test sentences works. Offline speech needs the desktop version with Whisper (next stage).
- Only the KJV is loaded. Modern wordings (NIV etc.) will not be recognised until we add translations and the meaning-based layer.
- The output window talks to the control page through the browser, so it must be opened from the same browser. A link that vMix/OBS can load as a Browser Source needs the desktop version (it adds a local server).
- No camera mixing, songs, or streaming yet. Those are the next stages.

## Editing it in Google AI Studio
index.html holds the whole interface and logic (about 300 lines). Paste it into AI Studio and ask for changes, for example "add a songs page like EasyWorship". Keep scripture.js and kjv.json beside it: scripture.js is the detection engine, built from the scripture-ai project.
