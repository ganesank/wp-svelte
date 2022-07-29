<script>
    import { navigate } from "svelte-routing";
    import { onMount } from "svelte";
    import { redirectURL } from "../store.js";
  
    import Comments from "../common/Comments.svelte";
    export let id;
    let data = [];
  
    let y;
    let x;
    const apiUrl = "https://ganesankar.co.in/wp-json/wp/v2/portfolio?slug=" + id;
    onMount(async function() {
      const response = await fetch(apiUrl);
      const dataArr = await response.json();
      data = dataArr[0];
    });
  </script>
  <style>
	.wp-block-image img {
		width:100%
	}
</style>
  <svelte:window bind:innerHeight={y} bind:scrollY={x} />
  <svelte:head>
    <title>Home Page</title>
  </svelte:head>
  <section class="templateux-hero" data-scrollax-parent="true">
    <!-- <div class="cover" data-scrollax="properties: { translateY: '30%' }"><img src="images/hero_2.jpg" /></div> -->
    <div class="container">
      <div class="row align-items-center justify-content-center intro">
        <div class="col-md-12 aos-init aos-animate" data-aos="fade-up">
          <div class="post-meta">
            <span>Posted in July 2, 2018</span>
            <span class="sep">•</span>
            <span>Posted by Josh Archibald</span>
          </div>
          <h1>
            {#if data.title}
              {@html data.title.rendered}
            {/if}
          </h1>
          <a href="#next" class="go-down js-smoothscroll" />
        </div>
      </div>
    </div>
  </section>
  
  <section class="templateux-portfolio-overlap mb-5" id="next">
    <div id="blog" class="site-section">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <p class="mb-5">
  
              <img
                src="images/img_1.jpg"
                alt=""
                class="img-fluid"
                data-pagespeed-url-hash="2601062986"
                onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
            </p>
            {#if data.content}
              {@html data.content.rendered}
            {/if}
            <div class="tag-widget post-tag-container mb-5 mt-5">
              <div class="tagcloud">
                <a href="#" class="tag-cloud-link">Work</a>
                <a href="#" class="tag-cloud-link">Bag</a>
                <a href="#" class="tag-cloud-link">Design</a>
                <a href="#" class="tag-cloud-link">Creative</a>
              </div>
            </div>
            <div class="pt-5 mt-5">
              {#if data.title}
              <Comments id={data.id} />
            {/if}
              
  
              <!-- END comment-list -->
  
            </div>
          </div>
          <!-- .col-md-8 -->
        
      </div>
    </div>
  </section>
  <section class="letter" />
  