<script>
  import { onMount } from "svelte";

  let images = [];

  export let image;
  export let size;

  export let alt;
  const apiUrl = "https://ganesankar.co.in/wp-json/wp/v2/media/" + image;
  let src = "";
  onMount(async function() {
    if (image) {
      const response = await fetch(apiUrl);
      images = await response.json();
      if (images && images.media_details && images.media_details.sizes && images.media_details.sizes[size]) {
        src = images.media_details.sizes[size].source_url || '';
      }
    } 
  });
</script>

{#if src}
  <img {src} {alt} class="img-fluid" />
{:else}
  <img
    src={`http://placehold.jp/24/dedede/ffffff/800x500.png?text=${alt}`}
    {alt}
    class="img-fluid" />
{/if}
