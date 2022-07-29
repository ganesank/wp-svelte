<script>
  import { onMount } from "svelte";
  import { Router, Route, Link, navigate } from "svelte-routing";
  import AOS from "aos";
  import Image from "svelte-image";
  import Home from "./routes/Home.svelte";
  import Page from "./routes/Page.svelte";
  import Blog from "./routes/Blog.svelte";
  import Category from "./routes/Category.svelte";
  import Tag from "./routes/Tag.svelte";
  
  import Post from "./routes/Post.svelte";
  import Portfolio from "./routes/Portfolio.svelte";
  import Public from "./routes/Public.svelte";
  import Protected from "./routes/Protected.svelte";
  import NotFound from "./routes/NotFound.svelte";

  import AppLoader from "./common/AppLoader.svelte";
  import { user, appInfo, userList, categoryList, tagsList } from "./store.js";
  let days = [
    "marvellous",
    "magnificent",
    "superb",
    "glorious",
    "sublime",
    "lovely",
    "delightful",
    "first-class",
    "super",
    "great",
    "amazing",
    "fantastic",
    "terrific",
    "tremendous",
    "sensational",
    "incredible",
    "heavenly",
    "gorgeous",
    "dreamy",
    "grand",
    "fabulous",
    "fab",
    "fabby",
    "fantabulous",
    "awesome",
    "magic",
    "ace",
    "cool",
    "mean",
    "mega",
    "mind-blowing",
    "A1",
    "sound",
    "marvy",
    "spanking",
    "brilliant",
    "smashing",
    "peachy",
    "neat",
    "bodacious",
    "beaut",
    "groovy",
    "divine",
    "capital",
    "champion",
    "cracking",
    "keen",
    "wondrous",
    "goodly",
  ];
  const random = Math.floor(Math.random() * days.length);
  const d = new Date();
  const n = d.getFullYear();

  $: isLoggedIn = !!$user;
  $: username = $user !== null ? $user.username : " there!";
  AOS.init();

  const appUrl = "https://ganesankar.co.in/wp-json/";
  const usersUrl = "wp/v2/users";
  const categoryUrl = "wp/v2/categories";
  const tagsUrl = "wp/v2/tags";
  let appData;
  let userData;
  let categoryData;
  let tagsData;

  onMount(async function() {
    const appResponse = await fetch(appUrl);
    appData = await appResponse.json();
    console.log(appData);
    delete appData.routes;
    appInfo.set(appData);

    //users
    const userResponse = await fetch(appUrl + usersUrl);
    userData = await userResponse.json();
    console.log(userData);
    userList.set(userData);

    //categories
    const categoryResponse = await fetch(appUrl + categoryUrl);
    categoryData = await categoryResponse.json();
    console.log(categoryData)
    categoryList.set(categoryData);

    //tags
    const tagsResponse = await fetch(appUrl + tagsUrl);
    tagsData = await tagsResponse.json();
    tagsList.set(tagsData);
  });
</script>

<style>

</style>

{#if appData && userData && tagsData && categoryData}
  <main data-animsition-in-class="fade-in" data-animsition-out-class="fade-out">
    <header class="templateux-navbar aos-init aos-animate" data-aos="fade-down">
      <div class="container-fluid">
        <div class="row">
          <div class="col-sm-3 col-3">
            <div class="site-logo">

              <Router>

                <Link css="animsition-link" to="/">Ganesan</Link>

              </Router>
            </div>
          </div>
          <div class="col-sm-9 col-9 text-right">
            <button
              class="hamburger hamburger--spin toggle-menu ml-auto
              js-toggle-menu"
              type="button">
              <span class="hamburger-box">
                <span class="hamburger-inner" />
              </span>
            </button>
            <nav class="templateux-menu js-templateux-menu" role="navigation">
              <ul class="list-unstyled">

                <Router>

                  <li class="d-md-none d-block active">
                    <Link css="animsition-link" to="/">Home</Link>
                  </li>
                  <li>
                    <Link css="animsition-link" to="/page/about">About</Link>
                  </li>
                  <li>
                    <Link css="animsition-link" to="/page/services">
                      Services
                    </Link>
                  </li>
                  <li>
                    <Link css="animsition-link" to="/portfolio">Works</Link>
                  </li>
                  <li>
                    <Link css="animsition-link" to="/blog">Blog</Link>
                  </li>
                  <li>
                    <Link css="animsition-link" to="/contact">Contact</Link>
                  </li>
                </Router>
              </ul>
            </nav>
          </div>
        </div>
      </div>
    </header>
    <Router>
      <Route path="/preface" component={Public} />
      <Route path="/page/:id" component={Page} />
      <Route path="/blog" component={Blog} />
      <Route path="/blog/:page" component={Blog} />

      <Route path="/category/:category" component={Category} />
      <Route path="/category/:category/:page" component={Category} />

      
      <Route path="/tags/:tag" component={Tag} />
      <Route path="/tags/:tag/:page" component={Tag} />

      <Route path="/post/:id" component={Post} />
      <Route path="/portfolio" component={Portfolio} />
      <Route path="/portfolio/:id" component={Portfolio} />
      <Route path="/letter" component={Protected} />
      <Route path="/" component={Home} />
    </Router>

  </main>
  <div class="clearfix" />
  <a
    class="templateux-section templateux-cta animsition-link mt-5 aos-init
    aos-animate"
    href="contact.html"
    data-aos="fade-up">
    <div class="container-fluid">
      <div class="cta-inner">
        <h2>
          <span class="words-1">
            Have
            <b data-superlatives="">a {days[random]}</b>
            day.
          </span>
          <span class="words-2">Let's chat we are good people.</span>
        </h2>
      </div>
    </div>
  </a>
  <footer class="templateux-footer">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-6 text-md-left text-center">
          <p>
            What's Meant To Be Will Always Find Its Way
            <br />
            This page is designed, built on
            <a href="hhttps://svelte.dev/" target="_blank">Svelte</a>
            , and backed by
            <a href="https://netlify.com" target="_blank">Netlify</a>
            .
            <br />
            Copyright &copy; {n}
            <a href="https://ganesankar.co.in" target="_blank">
              Ganesan Karuppaiya.
            </a>
          </p>
        </div>
        <div class="col-md-6 text-md-right text-center footer-social">
          <a href="#" class="p-3">
            <span class="icon-facebook2" />
          </a>
          <a href="#" class="p-3">
            <span class="icon-twitter2" />
          </a>
          <a href="#" class="p-3">
            <span class="icon-dribbble2" />
          </a>
          <a href="#" class="p-3">
            <span class="icon-instagram" />
          </a>
        </div>
      </div>
    </div>
  </footer>
{:else}
<AppLoader position="full" />{/if}
