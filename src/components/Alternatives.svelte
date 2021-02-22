<script>

    export let pokeNumber;
    export let answer;
    export let pokeList;

    let alternativeList = [pokeNumber];  
    let namedAlternatives = [];

    function SelectRandomNumber(forbiddenNumbers) {
        let tempNumber = Math.floor((Math.random() * 898) + 1);

        while (forbiddenNumbers.includes(tempNumber)) {
            tempNumber = Math.floor((Math.random() * 898) + 1);
        }

        return tempNumber;
    }

    for (let index = 0; index < 3; index++) {
        let randomNumber = SelectRandomNumber(alternativeList);

        alternativeList.push(randomNumber);
    }

    alternativeList.sort((a, b) => a -b);

    

</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
    }

    button {
        text-transform: capitalize;
        border: 2px solid black;
        background-color: white;
        padding: 8px 20px;
        border-radius: 20px;
        margin: 2px auto;
        cursor: pointer;
    }

    button:hover {
        border: 2px solid white;
        background-color: black;
        color: white;
    }

</style>

<div class="container">

    {#each pokeList as pokemon}
        {#if alternativeList.includes(pokemon.number)}
            <button on:click={answer}>{pokemon.name}</button>
        {/if}
    {/each}

    
</div>
