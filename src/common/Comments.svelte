<script>
  import { onMount } from "svelte";
  import moment from "moment";
  let list = [];
  export let id;

  const apiUrl = "http://www.ganesankar.co.in/wp-json/wp/v2/comments?post=" + id;
  let src = "";
  onMount(async function() {
    const response = await fetch(apiUrl);
    list = await response.json();
  });
</script>

{#if list && list.length > 0}
  <h3 class="mb-5">{list.length} Comments</h3>
  <ul class="comment-list">
    {#each list.reverse() as comment}
      <li class="comment">
        <div class="vcard bio" />
        <div class="comment-body">
          <h3>
            {@html comment.author_name}
          </h3>
          <div class="meta">
            {moment(comment.date).format('MMM DD, YYYY')} at {moment(comment.date).format('HH:mm')}
          </div>
          {@html comment.content.rendered}

        </div>
      </li>
    {/each}
  </ul>
{/if}
