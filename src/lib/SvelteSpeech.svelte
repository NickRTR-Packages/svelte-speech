<script>
    import { onMount } from "svelte";

    export let text = "Hello World";
    export let volume = 1;
    export let pitch = 1;
    export let rate = 1;

    let voices = [];
    /**
    * @type {SpeechSynthesisVoice | null}
    */
    let voice;

    onMount(() => {
        speechSynthesis.onvoiceschanged = () => {
            voices = speechSynthesis.getVoices();
            voice = voices[0];
        }
    })

    function play() {
        speechSynthesis.cancel(); // cancel playing text

        const speaker = new SpeechSynthesisUtterance(text);

        speaker.volume = volume;
        speaker.voice = voice;
        speaker.pitch = pitch;
        speaker.rate = rate;
        speechSynthesis.speak(speaker);
    }
</script>

<button on:click={play}>Play</button>