<script>
  import { navigate, Link } from "svelte-routing";
  import { onMount } from "svelte";
  import moment from "moment";
  import { redirectURL } from "../store.js";

  import PostImage from "../common/PostImage.svelte";
  let posts = [];
  let portfolio = [];
  let y;
  let x;
  const postApiUrl = "https://ganesankar.co.in/wp-json/wp/v2/posts";
  const portApiUrl = "https://ganesankar.co.in/wp-json/wp/v2/portfolio";
  onMount(async function() {
    const postresponse = await fetch(postApiUrl);
    const postsall = await postresponse.json();
    posts = postsall.slice(0, 6);


    const portResponse = await fetch(portApiUrl);
    const portsall = await portResponse.json();
    portfolio = portsall.slice(0, 6);
  });
</script>

<svelte:window bind:innerHeight={y} bind:scrollY={x} />
<svelte:head>
  <title>Home Page</title>
</svelte:head>
<section class="templateux-hero">
  <div class="container">
    <div class="row align-items-center justify-content-center intro">
      <div class="col-md-10 aos-init aos-animate" data-aos="fade-up">
        <h1>
          I'm Ganesan Karuppaiya
          <br />
          I build things for the web.
        </h1>
        <a href="#next" class="go-down js-smoothscroll" />
      </div>
    </div>
  </div>
</section>
<section class="templateux-section">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-4 aos-init aos-animate" data-aos="fade-up">
        <h2 class="section-heading mt-3">About me</h2>
      </div>
      <div
        class="col-md-8 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <div class="row">
          <div class="col-md-12">
            <h2 class="mb-5">
              In Short, Creative Designer, UI/UX Designer & Full Stack Developer
            </h2>
          </div>
        </div>
        <div class="row pt-sm-0 pt-md-5 mb-5">
          <div class="col-lg-12">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-monitor display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5"> In Short</h3>
                <p>
                  I'm a UI/ UX engineer based in Chennai, IN. Specializing in
                  building (and occasionally designing) exceptional,
                  high-quality websites and applications with clean and sharp
                  interfaces and innovator focusing business, users and success
                </p>
                <p>
                  I enjoys building things that live on the internet. I develop
                  exceptional websites and web apps that provide intuitive,
                  pixel-perfect user interfaces with ,efficient and modern
                  backends.
                </p>
              </div>
            </div>
          </div>
        </div>
        <!-- END row -->

      </div>
    </div>
  </div>
</section>
<section class="templateux-section">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-4 aos-init aos-animate" data-aos="fade-up">
        <h2 class="section-heading mt-3">What I Do</h2>
      </div>
      <div
        class="col-md-8 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <div class="row">
          <div class="col-md-12">
            <h2 class="mb-5">
              I develop exceptional websites and web apps that provide intuitive, pixel-perfect user interfaces with ,efficient and modern backends.
            </h2>
          </div>
        </div>
        <div class="row pt-sm-0 pt-md-5 mb-5">
          <div class="col-lg-12">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-monitor display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Designing and Branding</h3>
                <p>
                  Every great design starts with an simple idea and best way to present an idea is to visualise it. It makes your idea alive. In many cases, visualisation helps to understand the story of the business idea.  
                </p>
              </div>
            </div>
          </div>
          <div class="col-lg-12">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-command display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">UI/ UX Development</h3>
                <p>
                  It’s very important that all the fundamental parts are well defined and working This is where problem solving meets visual impact. I’ll unite products and users, design and experiences.
                </p>
              </div>
            </div>
          </div>
     
          <div class="col-lg-12">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-feather display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Rich Web Products</h3>
                <p>
                  It doesn’t stop with design. I can develop your product from visual concept to fully functional website with defined standards.
                </p>
              </div>
            </div>
          </div>
         
        </div>
        <!-- END row -->
      </div>
    </div>
  </div>
</section>

<section class="templateux-section mb-5">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-4 aos-init aos-animate" data-aos="fade-up">
        <h2 class="section-heading mt-3"> Recent works</h2>
      </div>
      <div class="col-md-8">

        <div class="row">

          {#if portfolio && portfolio.length > 0}
            {#each portfolio as post}
              <div class="col-lg-6" data-aos="fade-up"
              data-aos-delay="200">
                <Link
                  to={`portfolio/${post.slug}`}
                  css="post animsition-link aos-init"
                  href="blog-single.html"
                  >
                  <figure>
                    <PostImage
                      size="medium_large"
                      image={post.featured_media}
                      alt={post.title.rendered} />
                  </figure>
                  <div class="post-hover">
                    <div class="post-hover-inner">
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

        </div>
      </div>
    </div>
    <div class="row aos-init" data-aos="fade-up" data-aos-delay="400">
      <div class="col-md-8 ml-auto">
        <a href="blog.html" class="animsition-link">Read All Blog Posts</a>
      </div>
    </div>
  </div>
</section>

<section class="templateux-section mb-5">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-4 aos-init aos-animate" data-aos="fade-up">
        <h2 class="section-heading mt-3">Recent Blog Posts</h2>
      </div>
      <div class="col-md-8">

        <div class="row">

          {#if posts && posts.length > 0}
            {#each posts as post}
              <div class="col-lg-6" data-aos="fade-up"
              data-aos-delay="200">
                <Link
                  to={`post/${post.slug}`}
                  css="post animsition-link aos-init"
                  href="blog-single.html"
                  >
                  <figure>
                    <PostImage
                      size="medium_large"
                      image={post.featured_media}
                      alt={post.title.rendered} />
                  </figure>
                  <div class="post-hover">
                    <div class="post-hover-inner">
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

        </div>
      </div>
    </div>
    <div class="row aos-init" data-aos="fade-up" data-aos-delay="400">
      <div class="col-md-8 ml-auto">
        <a href="blog.html" class="animsition-link">Read All Blog Posts</a>
      </div>
    </div>
  </div>
</section>
