<script>
    import { navigate, Link } from "svelte-routing";
    import { onMount } from "svelte";
    import moment from "moment";
    import { tagsList } from "../store.js";
    import { fromArray } from "../common/Util.svelte";
    import PostImage from "../common/PostImage.svelte";
    export let location;
    $: location = location;
    export let page;
    export let tag;
    let posts = [];
    let y;
    let x;
    let pagination = page || 1;
    let categories;
    let pageTitle = '';
    onMount(async function() {
      const unsubscribe = tagsList.subscribe((value) => {
        categories = value;
      });
      if (categories && tag) {
        const id = fromArray(categories, "slug", tag, "id");
        pageTitle = fromArray(categories, "slug", tag, "name");
        const postApiUrl = `https://ganesankar.co.in/wp-json/wp/v2/posts?tags=${id}&per_page=10&page=${pagination}`;
        const postresponse = await fetch(postApiUrl);
        const postsall = await postresponse.json();
        posts = postsall;
      }
    });
  </script>
  
  <svelte:window bind:innerHeight={y} bind:scrollY={x} />
  <svelte:head>
    <title>Blog Page</title>
  </svelte:head>
  
  <section class="templateux-hero" data-scrollax-parent="true">
    <!-- <div class="cover" data-scrollax="properties: { translateY: '30%' }"><img src="images/hero_2.jpg" /></div> -->
    <div class="container">
      <div class="row align-items-center justify-content-center intro">
        <div class="col-md-10 aos-init aos-animate" data-aos="fade-up">
          <h1>Tag : {pageTitle}</h1>
          <p class="lead">Just another WordPress site</p>
          <a href="#next" class="go-down js-smoothscroll" />
        </div>
      </div>
    </div>
  </section>
  <section class="templateux-portfolio-overlap mb-5" id="next">
    <div class="container-fluid">
      <div class="row">
        {#if posts && posts.length > 0}
          {#each posts as post}
            <div
              class="col-md-6 aos-init aos-animate"
              data-aos="fade-up"
              data-aos-delay="200">
              <Link
                to={`post/${post.slug}`}
                css="post animsition-link aos-init"
                href="blog-single.html">
                <figure>
                  <PostImage
                    size="medium_large"
                    image={post.featured_media}
                    alt={post.title.rendered} />
                </figure>
                <div class="project-hover">
                  <div class="project-hover-inner">
                    <h2>
                      {@html post.title.rendered}
                    </h2>
                    <span>
                      {#if post.date}
                        {moment(post.date).format('MMM DD, YYYY')}
                      {/if}
                    </span>
                  </div>
                </div>
              </Link>
            </div>
          {/each}
        {/if}
  
        <div class="clearfix" />
        <div
          class="row pt-5 aos-init aos-animate"
          data-aos="fade-up"
          data-aos-delay="100">
          <div class="col-md-12 text-center">
            <!-- <a href="#" class="button button--red mb-5">Load More Posts...</a> -->
  
            <nav aria-label="Page navigation example">
              <ul class="pagination">
                <li class="page-item">
                  {#if pagination > 0}
                    <Link
                      to={`blog/${Number(pagination) === 2 ? '' : Number(pagination) - 1}`}
                      css="page-link">
                      Previous
                    </Link>
                  {:else}
                    <a class="button button--red" href="#" disabled>Previous</a>
                  {/if}
  
                </li>
                <li class="page-item">
  
                  {#if pagination > 0}
                    <Link to={`blog/${Number(pagination) + 1}`} css="page-link">
                      Next
                    </Link>
                  {:else}
                    <a class="page-link" href="#" disabled>Next</a>
                  {/if}
  
                </li>
              </ul>
            </nav>
          </div>
        </div>
      </div>
    </div>
  </section>
  