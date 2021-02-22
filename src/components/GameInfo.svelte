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
        <legend>lives: {lives}</legend>
    </div>
    <div class="score">
        <legend>score: {score}</legend>
    </div>
</div>