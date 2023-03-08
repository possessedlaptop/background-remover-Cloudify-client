<script lang="ts">
    import "two-up-element";
    import { originalImage, modifiedImage } from "./store";

    let processingImage = true
    let tries = 0
    let intervalId: any
    $: {
        if(processingImage){
            clearInterval(intervalId)
            intervalId = setInterval(() => {
                tries++
            }, 500)
        }
    }
</script>

<two-up>
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img src={$originalImage} alt="Original Image uploaded by user" />
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img
        on:load={() => (processingImage = false)}
        on:error={() => (processingImage = true)}
    src={`${$modifiedImage}&t=${tries}`} alt="Background removed Image uploaded by user" />
</two-up>

<a
    download
    href={$modifiedImage}
    class="block bg-blue-500 hover:bg-blue-700 text-xl text-center w-full font-bold text-white rounded-full px-4 py-2 mt-10"
>Download image without background</a>
