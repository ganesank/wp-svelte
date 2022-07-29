<script>
  import { navigate, Link } from "svelte-routing";
  import { onMount } from "svelte";
  import moment from "moment";
  import { categoryList, tagsList } from "../store.js";

  import Comments from "../common/Comments.svelte";
  import AuthorName from "../common/AuthorName.svelte";
  import { fromArray } from "../common/Util.svelte";
  export let id;
  let data = [];

  let y;
  let x;
  let categories;
  let tags;
  const apiUrl = "https://ganesankar.co.in/wp-json/wp/v2/posts?slug=" + id;
  onMount(async function() {
    const unsubscribe = categoryList.subscribe((value) => {
      categories = value;
    });
    const p = tagsList.subscribe((value) => {
      tags = value;
    });

    console.log(tags);
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
  <section class="templateux-hero" data-scrollax-parent="true">
    <!-- <div class="cover" data-scrollax="properties: { translateY: '30%' }"><img src="images/hero_2.jpg" /></div> -->
    <div class="container">
      <div class="row align-items-center justify-content-center intro">
        <div class="col-md-12 aos-init aos-animate" data-aos="fade-up">
          <div class="post-meta">
            <span>Posted in {moment(data.date).format('MMM DD, YYYY')}</span>
            <span class="sep">•</span>
            <span>
              Posted by
              <AuthorName author={data.author} />
            </span>
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
          <div class="col-md-8">
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
              {#if tags && data.tags && data.tags.length > 0}
                <div class="tagcloud">

                  {#each data.tags as tag}
                    {#if fromArray(tags, 'id', tag, 'name')}
                      <Link
                        to={`tags/${fromArray(tags, 'id', tag, 'slug')}`}
                        css="tag-cloud-link">
                        {fromArray(tags, 'id', tag, 'name')}
                      </Link>
                    {/if}
                  {/each}
                </div>
              {/if}
            </div>
            <div class="pt-5 mt-5">
              {#if data.title}
                <Comments id={data.id} />
              {/if}

              <!-- END comment-list -->

            </div>
          </div>
          <!-- .col-md-8 -->
          <div class="col-md-4 sidebar pl-md-5">
            <div class="sidebar-box">
              <form action="#" class="search-form">
                <div class="form-group">
                  <span class="icon fa fa-search" />
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Type a keyword and hit enter" />
                </div>
              </form>
            </div>
            <div class="sidebar-box">
              <div class="categories">
                <h3>Categories</h3>

                {#if categories && categories.length > 0}
                  {#each categories as category}
                    <li>
                      <Link to={`category/${category.slug}`}>
                        {category.name}
                      </Link>
                    </li>
                  {/each}
                {/if}

              </div>
            </div>

            {#if tags && tags.length > 0}
              <div class="sidebar-box">
                <h3>Tag Cloud</h3>
                <div class="tagcloud">

                  {#each tags as tag}
                    <Link to={`tags/${tag.slug}`} css="tag-cloud-link">
                      {tag.name}
                    </Link>
                  {/each}
                </div>
              </div>
            {/if}

          </div>
        </div>
      </div>
    </div>
  </section>
{/if}
