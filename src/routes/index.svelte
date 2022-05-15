<script>
    import SvelteSpeech from "$lib/SvelteSpeech.svelte";

    let text = "Hello World!";
    let volume = 1;
    let pitch = 1;
    let rate = 1;
    let voiceNumber = 0;

    /**
    * @type {SpeechSynthesisVoice[]}
    */
    let voices = [];

    /**
    * @type {(() => void) | undefined}
    */
    let play;
</script>

<body>
    <h1>svelte-speach</h1>
    <SvelteSpeech bind:text bind:volume bind:pitch bind:voices voice={voices[voiceNumber]} bind:play />
    
    <form>
        <label for="text">Input Text</label>
        <input type="text" name="text" placeholder="text" bind:value={text}>
        <label for="volume">Volume</label>
        <input type="range" name="volume" min="0" max="1" step=".1" bind:value={volume}>
        <label for="pitch">Pitch</label>
        <input type="range" name="pitch" min="0" max="2" step=".1" bind:value={pitch}>
        <label for="rate">Rate</label>
        <input type="range" name="rate" min=".2" max="2" step=".2" bind:value={rate}>

        <label for="voice">Choose voice</label>
        <select name="voice" bind:value={voiceNumber}>
            {#each voices as voice, i}
                <option value={i}>{voice.name}</option>
            {/each}
        </select>
        <button type="button" on:click={play}>Play</button>
    </form>
</body>

<style>
    body {
        text-align: center;
    }

    form {
        display: flex;
        flex-direction: column;
        max-width: 400px;
        margin-inline: auto;
    }

    label {
        margin-top: .5rem;
    }

    button {
        margin-top: 1rem;
        font-size: 1.2rem;
        border-radius: .5rem;
        font-weight: bold;
    }
</style>
