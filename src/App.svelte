<script>
  import { Router, Route, Link, navigate } from "svelte-routing";
  import AOS from "aos";
  import Image from "svelte-image";
  import Home from "./routes/Home.svelte";
  import Post from "./routes/Post.svelte";
  import Public from "./routes/Public.svelte";
  import Protected from "./routes/Protected.svelte";
  import NotFound from "./routes/NotFound.svelte";
  import { user, redirectURL } from "./store.js";
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
</script>

<style>

</style>

<main data-animsition-in-class="fade-in" data-animsition-out-class="fade-out">
  <header class="templateux-navbar aos-init aos-animate" data-aos="fade-down">
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-3 col-3">
          <div class="site-logo">
            
            <a href="index.html" class="animsition-link">Ganesan</a>
          </div>
        </div>
        <div class="col-sm-9 col-9 text-right">
          <button
            class="hamburger hamburger--spin toggle-menu ml-auto js-toggle-menu"
            type="button">
            <span class="hamburger-box">
              <span class="hamburger-inner" />
            </span>
          </button>
          <nav class="templateux-menu js-templateux-menu" role="navigation">
            <ul class="list-unstyled">
              <li class="d-md-none d-block active">
                <a href="index.html" class="animsition-link">Home</a>
              </li>
              <li>
                <a href="work.html" class="animsition-link">Work</a>
              </li>
           
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </header>
  <Router>
    <Route path="/preface" component={Public} />
    <Route path="/post/:id" component={Post} />
    <Route path="/letter" component={Protected} />
    <Route path="/" component={Home} />
  </Router>

</main>
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
          <a href="https://ganesan.xyz" target="_blank">Ganesan Karuppaiya.</a>
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
