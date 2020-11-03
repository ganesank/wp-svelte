<script>
  import { onMount } from "svelte";
  import moment from "moment";
  let list = [];
  export let id;

  const apiUrl = "http://www.ganesan.xyz/wp-json/wp/v2/comments?post=" + id;
  let src = "";
  onMount(async function() {
    console.log("role", apiUrl);
    const response = await fetch(apiUrl);
    list = await response.json();

    console.log(list);
  });
</script>

{#if list && list.length > 0}
  <h3 class="mb-5"> {list.length} Comments</h3>
  <ul class="comment-list">
  {#each list.reverse() as comment}
    <li class="comment">
      <div class="vcard bio">

      </div>
      <div class="comment-body">
        <h3>{@html comment.author_name}</h3>
        <div class="meta">{moment(comment.date).format('MMM DD, YYYY')} at {moment(comment.date).format('HH : MM')}</div>
        {@html comment.content.rendered}

      </div>
    </li>

  {/each}
  </ul>
{/if}
