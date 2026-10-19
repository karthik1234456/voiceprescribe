# VoicePrescribe

Remote consultation for weak internet. The doctor just talks, and the patient gets a clear Kannada prescription.

Built for **SYNERGIA 26, Problem Statement 3.2: Lightweight Telemedicine Prototype for Low-Bandwidth Coastal & Hill Talukas** (Theme: HealthTech, DeepTech & Inclusive Technology).

> **Decision-support aid, not a diagnostic device.** The doctor must confirm every prescription.

**Live demo:** _paste your deployment link here_
**Demo video:** _paste your video link here_

## The problem

- Specialists are far from coastal and hill talukas.
- Video calls break on weak internet, so most telemedicine tools fail.
- Many rural patients cannot read English drug names or know when to take each tablet.
- Handwritten prescriptions cause mistakes, especially with look-alike drug names.

## What it does

| Step | What happens |
|---|---|
| 1. Triage | Patient taps a problem in Kannada/English. Rules sort the case as urgent, normal or self-care and pick the doctor type. |
| 2. Adaptive call | Video drops to audio, then chat, without ending the consultation. With no network, messages are saved on the phone and sent later (store-and-forward). |
| 3. Voice prescription | The doctor talks as usual. Only medicine names, doses, timings and days are kept. The conversation is deleted right after extraction. |
| 4. Safety checks | Warns about unusually high doses and look-alike drug names. Low-confidence words are highlighted in yellow. |
| 5. Patient card | After the doctor confirms, the patient gets a Kannada card with sun and moon icons. Drug names stay in English to match the strip. A voice read-out and an SMS version are included. |

## Run it

It is a single static file with no build step.

1. Download or clone this repo.
2. Open `index.html` in Chrome.

Quick test: go to step 3, tap **Use sample**, then **Extract medicines**, then **Confirm and send**.

## Deploy

- **Vercel or Netlify:** import this repo and click Deploy. No settings are needed.
- **GitHub Pages:** Settings, Pages, deploy from the `main` branch, root folder.

## Tech

- Frontend: plain HTML, CSS and JavaScript (works as a lightweight web app on phones).
- Medicine matching: fuzzy matching with edit distance against a medicine list.
- Voice input: browser Web Speech API (Chrome). Typing always works.
- Read-aloud: browser speech synthesis (needs a Kannada voice on the device).
- Offline queue: browser local storage.
- No server and no database. Nothing is uploaded.

## Privacy

- No audio is recorded or saved by the app.
- The transcript is cleared as soon as medicines are extracted.
- Only the confirmed medicine list is kept, on the device.

See [docs/bandwidth-note.md](docs/bandwidth-note.md) for the bandwidth-optimisation techniques and [docs/architecture.md](docs/architecture.md) for the flow.

## Limitations

- The network speeds in step 2 are simulated. Real video calling is not built yet.
- The medicine list has 14 sample drugs. A full open Indian medicine list is planned.
- Speech-to-text uses the browser, which may need internet. On-device Whisper or Vosk is planned.
- Kannada wording should be reviewed by a native speaker before real use.

## Roadmap

- Real WebRTC video with automatic fallback
- On-device Kannada and English speech recognition
- Full open medicine database and drug-interaction checks
- Tulu and Hindi support
- Backend with doctor login and encrypted storage of confirmed prescriptions

## Team

_Add team member names here._

## License

MIT. See [LICENSE](LICENSE).
