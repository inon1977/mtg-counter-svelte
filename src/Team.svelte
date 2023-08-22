<script>
    export let team;
    export let score;
    export let gameOver;
    function add() {
        score += 1;
    }
    function minus() {
        score -= 1;
    }
</script>

<div style="border:dashed {team.toLowerCase()} 5px" class="col p-4">
    <h2 class:text-danger={team === 'Red'} class:text-primary={team === 'Blue'}>Team {team}: {score}</h2>
    <div class="text-center">
        <button disabled={gameOver} class="btn btn-success" on:click={add}>+</button>
        <button disabled={gameOver} class="btn btn-danger" on:click={minus}>-</button>
    </div>
</div>



