<script context="module">
  export function fromArray(a, b, c, d) {
    let i = a.findIndex((o) => o[b] == c);
    if (i > -1) {
      return a[i][d];
    }
    return undefined;
  }
</script>
