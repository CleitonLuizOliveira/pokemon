<script>
    export let pokeNumber;
    export let answer;
    export let pokeList;

    let alternativeList = [pokeNumber];  
    
    // const SelectRandomNumber = () => Math.floor(Math.random() * 899);

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
</style>

<div class="container">
    {#each alternativeList as pokemon}
        <button on:click={answer}>{pokemon}</button>
    {/each}
</div>
