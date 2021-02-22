<script>
    export let Replay;
</script>

<style>
    .container {
        text-align: center;
    }

    h1 {
        text-transform: uppercase;
        text-align: center;
        font-weight: bolder;
        font-size: 3rem;
    }

    button {
        border: 2px solid black;
        background-color: white;
        padding: 8px 20px;
        border-radius: 20px;
        cursor: pointer;
    }

    button:hover {
        border: 2px solid white;
        background-color: black;
        color: white;
    }
</style>

<div class="container">
    <h1>
        game<br>
        over
    </h1>
    <button on:click={Replay}>
        Play Again
    </button>
</div>