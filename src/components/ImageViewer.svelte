<script>

    export let pokeNumber;
    export let answered;

</script>

<style>
    img {
        width: 192px;
        image-rendering: optimizeSpeed;
        image-rendering: -moz-crisp-edges;          /* Firefox  */
        image-rendering: -o-crisp-edges;            /* Opera    */
        image-rendering: -webkit-optimize-contrast; /* Safari   */
        image-rendering: pixelated;                 /* Chrome   */
        user-select: none;
        pointer-events: none; 
    }

    .obscured {
        filter: brightness(0);
    }
</style>

<img src={`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokeNumber}.png`} alt="Quem é este Pokémon?" class={answered ? '' : 'obscured'}>

