<script>
  import { navigate ,Link} from "svelte-routing";
  import { onMount } from "svelte";
  import moment from "moment";
  import { redirectURL } from "../store.js";

  import PostImage from "../common/PostImage.svelte";
  let posts = [];

  let y;
  let x;
  const apiUrl = "http://ganesan.xyz/wp-json/wp/v2/posts";
  onMount(async function() {
    console.log("role", apiUrl);
    const response = await fetch(apiUrl);
    const postsall = await response.json();
    posts = postsall.slice(0, 6);
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
          We are Strategy. A digitally minded creative agency based in NYC.
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
        <h2 class="section-heading mt-3">What We Do</h2>
      </div>
      <div
        class="col-md-8 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <div class="row">
          <div class="col-md-12">
            <h2 class="mb-5">
              Far far away, behind the word mountains, far from the countries
              Vokalia and Consonantia.
            </h2>
          </div>
        </div>
        <div class="row pt-sm-0 pt-md-5 mb-5">
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-monitor display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Web Development</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-command display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Brand identity</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
        </div>
        <!-- END row -->
        <div class="row clearfix">
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-feather display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Copywriting</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-shopping-cart display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">eCommerce</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
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
        <h2 class="section-heading mt-3">What We Do</h2>
      </div>
      <div
        class="col-md-8 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <div class="row">
          <div class="col-md-12">
            <h2 class="mb-5">
              Far far away, behind the word mountains, far from the countries
              Vokalia and Consonantia.
            </h2>
          </div>
        </div>
        <div class="row pt-sm-0 pt-md-5 mb-5">
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-monitor display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Web Development</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-command display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Brand identity</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
        </div>
        <!-- END row -->
        <div class="row clearfix">
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-feather display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">Copywriting</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
                </p>
              </div>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="media templateux-media mb-4">
              <div class="mr-4 icon">
                <span class="icon-shopping-cart display-3" />
              </div>
              <div class="media-body">
                <h3 class="h5">eCommerce</h3>
                <p>
                  Far far away, behind the word mountains, far from the
                  countries Vokalia and Consonantia, there live the blind texts.
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
<section class="templateux-portfolio-overlap" id="next">
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-6 aos-init aos-animate" data-aos="fade-up">
        <a class="project animsition-link" href="work-single.html">
          <figure>

            <img
              src="images/img_1.jpg"
              alt="Free Template"
              class="img-fluid"
              data-pagespeed-url-hash="2601062986"
              onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
          </figure>
          <div class="project-hover">
            <div class="project-hover-inner">
              <h2>Canvas Tote Bag</h2>
              <span>View Case Study</span>
            </div>
          </div>
        </a>
      </div>
      <div
        class="col-md-6 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <a class="project animsition-link" href="work-single.html">
          <figure>
            <img
              src="images/img_2.jpg"
              alt="Free Template"
              class="img-fluid"
              data-pagespeed-url-hash="2895562907"
              onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
          </figure>
          <div class="project-hover">
            <div class="project-hover-inner">
              <h2>Work Hard, Play Hard</h2>
              <span>View Case Study</span>
            </div>
          </div>
        </a>
      </div>
    </div>
    <!-- END row -->
    <div class="row">
      <div class="col-lg-4 col-md-6 aos-init aos-animate" data-aos="fade-up">
        <a class="project animsition-link" href="work-single.html">
          <figure>
            <img
              src="images/img_3.jpg"
              alt="Free Template"
              class="img-fluid"
              data-pagespeed-url-hash="3190062828"
              onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
          </figure>
          <div class="project-hover">
            <div class="project-hover-inner">
              <h2>Moon High Res</h2>
              <span>View Case Study</span>
            </div>
          </div>
        </a>
      </div>
      <div
        class="col-lg-4 col-md-6 aos-init aos-animate"
        data-aos="fade-up"
        data-aos-delay="100">
        <a class="project animsition-link" href="work-single.html">
          <figure>
            <img
              src="images/img_4.jpg"
              alt="Free Template"
              class="img-fluid"
              data-pagespeed-url-hash="3484562749"
              onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
          </figure>
          <div class="project-hover">
            <div class="project-hover-inner">
              <h2>H20 Water Bottle</h2>
              <span>View Case Study</span>
            </div>
          </div>
        </a>
      </div>
      <div
        class="col-lg-4 col-md-6 aos-init"
        data-aos="fade-up"
        data-aos-delay="200">
        <a class="project animsition-link" href="work-single.html">
          <figure>
            <img
              src="images/img_5.jpg"
              alt="Free Template"
              class="img-fluid"
              data-pagespeed-url-hash="3779062670"
              onload="pagespeed.CriticalImages.checkImageForCriticality(this);" />
          </figure>
          <div class="project-hover">
            <div class="project-hover-inner">
              <h2>Creatsy Mailing Box</h2>
              <span>View Case Study</span>
            </div>
          </div>
        </a>
      </div>
    </div>
    <!-- END row -->
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
              <div class="col-lg-6">
                <Link
                  to={`post/${post.id}`}
                  css="post animsition-link aos-init"
                  href="blog-single.html"
                  data-aos="fade-up"
                  data-aos-delay="200">
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
<section class="letter" />
