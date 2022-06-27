# svelte-speech

1. npm install svelte-speech
2. in your script add: `import SvelteSpeech from "svelte-speech";`
3. In your HTML add: `<SvelteSpeech text={"Hello World"} bind:play />`

## Optional properties

- volume: range: 0 - 1
- Pitch: range 0 - 2
- Rate (speed): 0.2 - 2
- bind:voices: bind all available voices to a variable
- `voice=voices[indexOfSelectedVoice]`: select one of the available voices
