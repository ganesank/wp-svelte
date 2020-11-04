<script>
  import { onMount } from "svelte";
  export let author;

  const apiUrl = "http://ganesan.xyz/wp-json/wp/v2/users/" + author;
  let name = "";
  console.log(author)
  onMount(async function() {
    if (author) {
      const response = await fetch(apiUrl);
      const     data = await response.json();
      if (data && data.name) {
        name = data.name;
      }
    }
  });
</script>

<span>{name}</span>
