<script>
    export let lives;
    export let score;
</script>

<style>
    .container {
        display: flex;
        place-content: space-between;
        width: 250px;
    }

    .score {
        text-align: right;
    }
</style>

<div class="container">
    <div class="lives">
        <legend>lives</legend>
        <h2>{lives}</h2>
    </div>
    <div class="score">
        <legend>score</legend>
        <h2>{score}</h2>
    </div>
</div>