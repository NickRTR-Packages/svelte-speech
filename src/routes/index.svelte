<script>
    import SvelteSpeech from "$lib/SvelteSpeech.svelte";

    /**
    * @type {SpeechSynthesisVoice[]}
    */
    let voices = [];

    /**
    * @type {(() => void) | undefined}
    */
    let play;
</script>

<h1>svelte-speach</h1>
<SvelteSpeech text={"Hello World!"} bind:voices voice={voices[2]} bind:play={play} />

<button on:click={play}>Play</button>