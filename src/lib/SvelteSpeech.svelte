<script>
    import { onMount } from "svelte";

    export let text = "Hello World";
    export let volume = 1;
    export let pitch = 1;
    export let rate = 1;

    /**
    * @type {SpeechSynthesisVoice[]} 
    */
    export let voices = [];
    /**
    * @type {SpeechSynthesisVoice}
    */
    export let voice;

    onMount(() => {
        speechSynthesis.onvoiceschanged = () => {
            voices = speechSynthesis.getVoices();
            voice = voices[0];
        }
    })

    export const play = () => {
        speechSynthesis.cancel(); // cancel playing text

        const speaker = new SpeechSynthesisUtterance(text);

        speaker.volume = volume;
        speaker.voice = voice;
        speaker.pitch = pitch;
        speaker.rate = rate;
        speechSynthesis.speak(speaker);
    }
</script>