<script>
    import Gallery from "./lib/Gallery.svelte";
    import Toolbar from "./lib/Toolbar.svelte";
    import {count} from "./stores/count.js";
    import {onMount} from "svelte";

    let pageNumber;
    const numImages = 6;
    const images = [];
    const imageUrl = (id) => `https://picsum.photos/id/${id}/300/300`;

    async function getImages() {
        const imageResponseBlob = await fetch(`https://picsum.photos/v2/list?page=${pageNumber}&limit=${numImages}`)
        const imageResponse = await imageResponseBlob.json()
        const output = imageResponse.map(image => {
            return {
                url: imageUrl(image.id),
                alt: image.author
            }
        });
        console.log(output)
        images.length = 0;
        images.push(...output);
    }
    const unsubscribe = count.subscribe(n => pageNumber = n)
    function updateCountCallback(event) {
        switch (event.detail) {
            case 'increment':
                count.update(n => n + 1);
                getImages()
        }
    }
    onMount(() => {
        getImages()
    });
</script>

<main>
    <Gallery {images}/>
    <Toolbar on:updateCount="{updateCountCallback}"/>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>
