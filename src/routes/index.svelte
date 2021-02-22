<script>
	import ImageViewer from "../components/ImageViewer.svelte";	

	const SelectRandomNumber = () => Math.floor(Math.random() * 899);

	let pokeNumber = SelectRandomNumber();

	console.log(pokeNumber);
</script>

<svelte:head>
	<title>Quem é este Pokémon?</title>
</svelte:head>

<h1>Quem é este Pokémon?</h1>
<ImageViewer {pokeNumber} />
