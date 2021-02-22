<script>
    import pokeball from '../images/pokeball.png';

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

    legend {
        padding: 0;
        margin: 0;
    }

    h2 {
        font-weight: bolder;
        font-size: 32px;
        margin: 0;
        padding: 0;
    }

    .life-counter {
        display: block;
        height: 32px;
        width: 96px;
        background-position: top right;
        background-repeat: repeat;
    }


</style>

<div class="container">
    <div class="lives">
        <legend>lives: </legend>
        <div style="background-image: url({pokeball}); width: {32 * lives}px" class="life-counter"></div>
    </div>
    <div class="score">
        <legend>score:</legend>
        <h2>{score}</h2>
    </div>
    
</div>