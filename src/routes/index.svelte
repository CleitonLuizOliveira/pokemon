<script>
	import ImageViewer from "../components/ImageViewer.svelte";	
	import Alternatives from "../components/Alternatives.svelte";	

	export async function FetchPokemon() {
        const response = await fetch('pokemon.json');
        const responseJson = await response.json();
        return responseJson.pokemon;
    }

	let answered = false;

	const SelectRandomNumber = () => Math.floor(Math.random() * 899);

	function answer() {
		answered = true;
	}

	let pokeNumber = SelectRandomNumber();

	let pokeList = FetchPokemon();

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
	<ImageViewer {pokeNumber} {answered} />
	<Alternatives {pokeNumber} {answer} />
</main>

