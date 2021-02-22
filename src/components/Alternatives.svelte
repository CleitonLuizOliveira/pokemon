<script>
    export let pokeNumber;
    export let answer;
    export let answered;
    export let pokeList;

    let alternativeList = [];  

    function SelectRandomNumber(forbiddenNumbers) {
        let tempNumber = Math.floor((Math.random() * 898) + 1);

        while (forbiddenNumbers.includes(tempNumber)) {
            tempNumber = Math.floor((Math.random() * 898) + 1);
        }

        return tempNumber;
    }

    function FillList(firstElement) {
        alternativeList = [];
        alternativeList.push(firstElement);

        for (let index = 0; index < 8; index++) {
            let randomNumber = SelectRandomNumber(alternativeList);

            alternativeList.push(randomNumber);
        }

        alternativeList.sort((a, b) => a -b); 
    }

    $: FillList(pokeNumber);

</script>

<style>
    .container {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: 360px;
        place-content: center;
        place-items: center;
    }

    button {
        text-transform: capitalize;
        border: 2px solid black;
        background-color: white;
        padding: 4px 20px;
        border-radius: 20px;
        margin: 4px;
        cursor: pointer;
    }

    button:hover {
        border: 2px solid white;
        background-color: black;
        color: white;
    }

    button:disabled {
        background-color: tomato;
        border: 2px solid tomato;
        color: white;
    }

    .right_answer:disabled {
        background-color: green;
        border: 2px solid green;
        color: white;
    }

</style>

<div class="container">

    {#each pokeList as pokemon}
        {#if alternativeList.includes(pokemon.number)}
            <button on:click={() => answer(pokemon.number)} disabled={answered} class={pokemon.number === pokeNumber ? "right_answer" : ""}>
                {pokemon.name}
            </button>
        {/if}
    {/each}
    
</div>
