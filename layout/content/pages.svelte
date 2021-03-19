<script>
  export let title, description, content;
  import Uses from "../components/source.svelte";
  import { scale } from "svelte/transition";
</script>

{#key content}  
<div in:scale={{ delay: 300 }} out:scale>
<h1>{title}</h1>

<div>
  {#each description as paragraph}
    <p>{@html paragraph}</p>
  {/each}
</div>

<Uses {content} />

<p><a href="/">Back home</a></p>

</div>
{/key}