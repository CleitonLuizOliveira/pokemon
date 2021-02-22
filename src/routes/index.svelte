<script>
	import { onMount } from 'svelte';

	import ImageViewer from "../components/ImageViewer.svelte";	
	import Alternatives from "../components/Alternatives.svelte";	
	import Result from '../components/Result.svelte';

	let answered = false;
	let rightAnswer = false;

	const SelectRandomNumber = () => Math.floor((Math.random() * 898) + 1);

	let pokeNumber = SelectRandomNumber();

	let pokeList = [];

	onMount(async () => {
		const response = await fetch(`pokemon.json`);
		const responseJson = await response.json();
		pokeList =  responseJson.pokemon;
	});

	function answer(number) {
		answered = true;

		if (number === pokeNumber) {
			rightAnswer = true;
		} else {
			rightAnswer = false;
		}
	}

</script>

<svelte:head>
	<title>Who's That Pokémon?</title>
</svelte:head>

<style>
	main {
		display: flex;
		flex-direction: column;
		place-content: center;
		place-items: center;
	}

	h1 {
		font-weight: bold;
	}
</style>


<main>
	<h1>Who's That Pokémon?</h1>
	<ImageViewer {pokeNumber} {answered}  />
	<Result {rightAnswer} {answered} />
	<Alternatives {pokeNumber} {answer} {answered} {pokeList}/>
</main>

