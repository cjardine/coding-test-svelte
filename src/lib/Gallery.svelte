<script>
    import Image from "./Image.svelte";

    export let images;
</script>

<ul>
    {#each images as image}
        <Image {image}/>
    {/each}
</ul>
<style>
    ul {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        margin: 0 auto;
        padding: 0;
        max-width: 800px;
        column-gap: 12px;
        row-gap: 12px;

    }

    @media (max-width: 600px) {
        ul {
            display: grid;
            grid-template-columns: 1fr;
            margin: 0 auto;
            padding: 0;
            column-gap: 20px;
            row-gap: 20px;

        }
    }

</style>
