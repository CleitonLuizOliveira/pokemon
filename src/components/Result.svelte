<script>
    export let answered;
    export let rightAnswer;
</script>

<style>
    h2 {
        margin: 30px auto;
        font-weight: bold;        
    }

    .correct {
        color: green;
    }

    .wrong {
        color: tomato;
    }
</style>

{#if answered}
    {#if rightAnswer}
        <h2 class="correct">Correct!</h2>
    {:else}
        <h2 class="wrong">Wrong!</h2>
    {/if}
{:else}   
    <h2>Who's that Pokémon?</h2>
{/if}	