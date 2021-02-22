<script>
	import { onMount } from 'svelte';

	import ImageViewer from "../components/ImageViewer.svelte";	
	import Alternatives from "../components/Alternatives.svelte";	

	let answered = false;

	const SelectRandomNumber = () => Math.floor((Math.random() * 898) + 1);

	function answer() {
		answered = true;
	}

	let pokeNumber = SelectRandomNumber();

	let pokeList = [];

	onMount(async () => {
		const response = await fetch(`pokemon.json`);
		const responseJson = await response.json();
		pokeList =  responseJson.pokemon;
	});

</script>

<svelte:head>
	<title>Quem é este Pokémon?</title>
</svelte:head>

<style>
	main {
		display: flex;
		flex-direction: column;
		place-content: center;
		place-items: center;
	}
</style>


<main>
	<h1>Quem é este Pokémon?</h1>
	<ImageViewer {pokeNumber} {answered}  />
	<Alternatives {pokeNumber} {answer} {pokeList}/>
</main>

