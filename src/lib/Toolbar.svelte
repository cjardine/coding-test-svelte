<script>

    import {createEventDispatcher} from "svelte";

    const increment = createEventDispatcher();

</script>

<div class="tool-bar">
    <button on:click="{() => increment('updateCount', 'increment')}">Generate</button>
</div>


<style>
    .tool-bar {
        margin: 70px auto;
        padding: 70px;
        border-top: 1px solid #dadada;
        width: auto;
    }

    button {
        padding: 10px 20px;
        border: transparent 1px solid;
        border-radius: 4px;
        background-color: #00aaee;
        color: white;
    }
</style>
