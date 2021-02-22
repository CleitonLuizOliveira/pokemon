<script>
    export let answered;
    export let rightAnswer;
</script>

<style>
    h2 {
        margin: 30px auto;
        font-weight: bold;
        color: tomato;
    }

    .correct {
        color: green;
    }
</style>

{#if answered}
    {#if rightAnswer}
        <h2 class="correct">Correct!</h2>
    {:else}
        <h2>Wrong!</h2>
    {/if}
{/if}	