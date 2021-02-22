<script>

    export let pokeNumber;

    async function FetchPokemonImage() {
		const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokeNumber}/`);
		const pokemon = await response.json();

        if (response.ok) {
			return pokemon;
		} else {
			throw new Error(text);
		}
		
	}

    let promise = FetchPokemonImage();


</script>

<style>
    main {
        text-align: center;
        display: flex;
        place-content: center;
        place-items: center;
        flex-direction: column;
    }

    img {
        width: 384px;
        image-rendering: optimizeSpeed;             /* STOP SMOOTHING, GIVE ME SPEED  */
        image-rendering: -moz-crisp-edges;          /* Firefox                        */
        image-rendering: -o-crisp-edges;            /* Opera                          */
        image-rendering: -webkit-optimize-contrast; /* Chrome (and eventually Safari) */
        image-rendering: pixelated; /* Chrome */
        image-rendering: optimize-contrast;         /* CSS3 Proposed                  */
    }

    .obscured {
        filter: brightness(0)
    }
</style>

<main>
    {#await promise}
	<p>Aguarde...</p>
    {:then pokemon}
        <img src={pokemon.sprites.front_default} alt="Quem é este Pokémon?" class="obscured">
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
</main>

