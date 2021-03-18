<script>
  export let title, description, content;
  import Uses from "../components/source.svelte";
  import { onMount } from "svelte";
  import { slide } from "svelte/transition";

  onMount(async () => {
  });
</script>

<div in:slide={{ delay: 300 }} out:slide={{ delay: 300}}>
<h1>{title}</h1>

<div>
  {#each description as paragraph}
    <p>{@html paragraph}</p>
  {/each}
</div>

<Uses {content} />

<p><a href="/">Back home</a></p>

</div>