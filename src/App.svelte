<script>
	import WordData from "./components/WordData.svelte";

	let word = "";
	let wordData = null;
	let receive = false;

	async function getWords() {
		let res = await fetch("https://api.dictionaryapi.dev/api/v2/entries/en/"+word)
		
		let data = await res.json();

		if (Array.isArray(data)) {
			wordData = data[0];
			receive = !receive;
		}

		// Clear input
		document.querySelector("input").value = ""
	}
</script>

<main class="p-2">
	<form on:submit|preventDefault={getWords}>
		<label for="search">Search Word</label>
		<input type="text" placeholder="Type word here" bind:value={word}>
		<button class="btn btn-primary" type="submit">Search</button>
	</form>

	{#if receive}
		<WordData wordData={wordData} />
		{:else}
		<p>No word searched</p>
	{/if}
</main>

<style>
	form label {
		display: block;
	}
</style>