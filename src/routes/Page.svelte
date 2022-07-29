<script>
  import { navigate } from "svelte-routing";
  import { onMount } from "svelte";
  import PostImage from "../common/PostImage.svelte";
  import { redirectURL } from "../store.js";

  import Comments from "../common/Comments.svelte";
  export let id;
  let data = [];

  let y;
  let x;
  const apiUrl = "https://ganesankar.co.in/wp-json/wp/v2/pages?slug=" + id;
  onMount(async function() {
    const response = await fetch(apiUrl);
    const dataArr = await response.json();
    data = dataArr[0];
  });
</script>

<svelte:window bind:innerHeight={y} bind:scrollY={x} />
<svelte:head>
  <title>Home Page</title>
</svelte:head>
{#if data.title}
<!-- END templateux-navbar -->
<section class="templateux-hero overlay" data-scrollax-parent="true">
  <div class="cover" style="transform: translateZ(0px) translateY(25.6286%);">
    <PostImage
    size="medium_large"
    image={data.featured_media}
    alt={data.title.rendered} />
  </div>
  <div class="container">
    <div class="row align-items-center justify-content-center intro">
      <div class="col-md-10 aos-init aos-animate" data-aos="fade-up">
        <h1>
          {#if data.title}
            {@html data.title.rendered}
          {/if}
        </h1>
        <p class="lead">
          
        </p>
        <a href="#next" class="go-down js-smoothscroll" />
      </div>
    </div>
  </div>
</section>
<!-- END templateux-hero -->

<section class="templateux-section">
  <div class="container py-5 aos-init aos-animate" data-aos="fade-up">
    <div class="row">
      <div class="col-md-12 clearfix mb-3">
        {#if data.content}
          {@html data.content.rendered}
        {/if}
      </div>
    </div>
  </div>

</section>
<div class="clearfix mb-3">
    &nbsp;
  </div>
  {/if}