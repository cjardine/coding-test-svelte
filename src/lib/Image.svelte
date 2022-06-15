<script>
    export let image;
</script>


<li>
    <img src="{image.url}" alt="{image.alt}"/>
</li>


<style>
    li {
        list-style: none;
    }

    img {
        width: 100%;
        display: block;
        border: 1px solid transparent;
        border-radius: 4px;
        overflow: hidden;
    }
</style>
