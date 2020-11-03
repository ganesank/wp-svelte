<script>
  import { navigate } from "svelte-routing";
  import { onMount } from "svelte";
  import { user,redirectURL } from "../store.js";
  const apiURL =
    "/.netlify/functions/thumbelina";
  let data = [];
  let dataW = [];
  const key = __myapp.env.API_KEY || "fnAD3fyPz9ACB-";

  const simpleCrypto = new SimpleCrypto(key);


  export let location;
  let datax;
  let y;
  let x;
  let cats;
  function handlePrivateRoute() {
    redirectURL.setRedirectURL(location.href);
    navigate("/", {
      replace: true,
    });

    Swal.fire({
      title: "You are not authenticated",
      text: "Please log in or sign up to view this page",
      type: "error",
      allowOutsideClick: false,
      confirmButtonText: "Will do!",
    });
  }

  onMount(async function() {
    console.log('role', $user)
    const response = await fetch(apiURL);
   const dataX = await response.json();
    const decipherText = simpleCrypto.decrypt(dataX.data)
   
   data = decipherText[0].data.attachments;
  });
</script>

<svelte:window bind:innerHeight={y} bind:scrollY={x} />
<svelte:head>
  <title>Message : It's not goodbye again</title>
</svelte:head>

{#if $user && $user.username}

  <section class="letter">
    {#if data && data.length > 0}
      {#each data as cat}
        <div>
          <h4>{cat.name}</h4>
          {#if cat.content}
            {@html cat.content}
          {/if}
          {#if cat.array && cat.array.length > 0}
            <div />

            {#each cat.array as ari}
              <div class={`TimelineItem ${ari.type} `}>
                <div class="TimelineItem-badge-Container ">
                  {#if ari.class && ari.class.length > 0}
                    {#each ari.class as ac}
                      <div class={`TimelineItem-badge bg-red text-white `}>
                        <i class={`las ${ac} `} />
                      </div>
                    {/each}
                  {:else}
                    <div class={`TimelineItem-badge bg-red text-white `} />
                  {/if}
                </div>
                <div class="TimelineItem-body">
                  {@html ari.content}
                </div>
              </div>
            {/each}
          {/if}

          <hr />
        </div>
      {/each}
    {/if}
  </section>
{:else}{handlePrivateRoute()}{/if}
