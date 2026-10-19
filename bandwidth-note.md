# Bandwidth-optimisation note

| Network | Mode | Approx. data use |
|---|---|---|
| Good | Video call | about 500 kbps |
| Weak | Audio only | about 24 kbps |
| Very weak | Short chat messages | about 1 kbps |
| None | Store-and-forward on the device | 0 until the network returns |

Techniques used:

1. **Graceful degradation:** the consultation moves video, then audio, then chat, and never ends.
2. **Store-and-forward:** messages are queued in local storage and sent when the network returns.
3. **Text instead of audio:** only the medicine name, dose, timing and days are kept, a few hundred bytes instead of a recording.
4. **Plain SMS fallback:** the prescription fits in one short SMS.
5. **No server round trips for triage:** rules run in the browser.
6. **Single small file:** the whole app is one lightweight page.

Planned: compress photos before upload, and run speech recognition on the device.
