<script>
	import ImageViewer from "../components/ImageViewer.svelte";	
	import Alternatives from "../components/Alternatives.svelte";	

	const SelectRandomNumber = () => Math.floor(Math.random() * 899);

	let pokeNumber = SelectRandomNumber();

	console.log(pokeNumber);
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
	<ImageViewer {pokeNumber} />
	<Alternatives {pokeNumber} />
</main>

