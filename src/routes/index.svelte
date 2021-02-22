<script>
	import { onMount } from 'svelte';

	import ImageViewer from "../components/ImageViewer.svelte";	
	import Alternatives from "../components/Alternatives.svelte";	
	import Result from '../components/Result.svelte';
	import GameInfo from '../components/GameInfo.svelte';
	import GameOver from '../components/GameOver.svelte';

	let lives = 0;
	let score = 0;
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
			score = score + 1;
		} else {
			rightAnswer = false;
			lives = lives -1;
		}
	}

	function NextQuestion() {
		pokeNumber = SelectRandomNumber();
		answered = false;
		rightAnswer = false;
	}

	function Replay() {
		lives = 3;
		score = 0;
		answered = false;
		rightAnswer = false;
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

	button {
		margin-top: 40px;
        border: 2px solid black;
        background-color: white;
        padding: 8px 20px;
        border-radius: 20px;
        cursor: pointer;
    }

    button:hover {
        border: 2px solid white;
        background-color: black;
        color: white;
    }

</style>


<main>
	{#if lives > 0}
		<GameInfo {score} {lives} />
		<ImageViewer {pokeNumber} {answered}  />
		<Result {rightAnswer} {answered} />
		<Alternatives {pokeNumber} {answer} {answered} {pokeList}/>

		{#if answered}
			<button on:click={NextQuestion}>Next Pokémon</button>
		{/if}
	{:else}
		<GameOver {Replay} />
	{/if}
	
</main>

