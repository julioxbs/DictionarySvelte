<script>
    export let wordData = null;
    
    let resume = {
        word: wordData.word,
        meanings: wordData.meanings,
        phonetics: wordData.phonetics[0]
    }

    function playAudio(src) {
        let audio = new Audio(src);
        audio.play()
    }
</script>

<div class="word-data">
    <h3>{resume.word}</h3>

    {#if wordData.phonetics}
        <div class="audios">
                <div class="audio d-flex">
                    <p>{resume.phonetics.text}</p>
                    <i class="btn fa fa-play-circle" on:click={() => playAudio(resume.phonetics.audio)}></i>
                </div>
        </div>
    {/if}

    {#each wordData.meanings as meaning}
        <div>&bull; {meaning.partOfSpeech}</div>

        <div class="definitions">
            {#each meaning.definitions as data}
                <p>Definitions: <b>{data.definition}</b></p>

                {#if data.example}
                    <p>Example: <i>{data.example}</i></p>
                {/if}
            {/each}
        </div>
    {/each}
</div>

<style>

</style>