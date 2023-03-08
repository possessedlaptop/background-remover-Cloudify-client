<script lang="ts">
  import { ImageStatus } from "../types.d";
  import CloudinaryLogo from "./CloudinaryLogo/CloudinaryLogo.svelte";
  import StepEdit from "./StepEdit.svelte";
  import StepUpload from "./StepUpload.svelte";
  import { imageStatus } from "./store.js";
</script>

<div class="max-w-xl m-auto grid grid-cols-1 place-content-center w-full h-screen p-4">
  <header class="flex justify-center py-10">
    <h1 class="text-2l font-bold text-blue-900 tracking-tighter">
      Remove<span class="text-blue-600">Background</span> by CouchSloth
    </h1>
  </header>

  <main class="w-full block">
    {#if $imageStatus == ImageStatus.READY || $imageStatus == ImageStatus.UPLOADING}
      <StepUpload />
    {:else if $imageStatus == ImageStatus.DONE}
      <StepEdit />
    {/if}
  </main>

  <footer class="flex justify-center items-center gap-x-2 font-semibold pt-10">
    Powered by <a href="https://cloudinary" target="_blank" rel="noreferrer"
      ><CloudinaryLogo /></a
    >
  </footer>
</div>

<!-- All credits to Midu and his video https://www.youtube.com/watch?v=ODyG8s7Gx1M-->
