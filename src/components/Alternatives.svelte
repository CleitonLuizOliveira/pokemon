<script>
    export let pokeNumber;
    export let answer;

    let alternativeList = [pokeNumber];  
    
    const SelectRandomNumber = () => Math.floor(Math.random() * 899);

    for (let index = 0; index < 3; index++) {
        let randomNumber = SelectRandomNumber();
        
        if (alternativeList.includes(randomNumber)) {
            randomNumber = SelectRandomNumber();
        } 

        alternativeList.push(randomNumber);
    }

</script>

<div class="container">
    {#each alternativeList as pokemon}
        <button on:click={answer}>{pokemon}</button>
    {/each}
</div>