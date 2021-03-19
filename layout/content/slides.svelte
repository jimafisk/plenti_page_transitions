<script>
  export let title, description, order, content;
  import { scale } from "svelte/transition";
</script>

{#key content}  
<div id="slides" in:scale={{ delay: 300 }} out:scale>
<h1>{title}</h1>

<a class="controls prev" href="/slides/{parseFloat(order)-1}">Previous</a>

<div>
  {#each description as paragraph}
    <p>{@html paragraph}</p>
  {/each}
</div>

<a class="controls next" href="/slides/{parseFloat(order)+1}">Next</a>

<a class="exit" href="/">Exit Slides</a>

</div>
{/key}

<style>
    #slides {
        display: flex;
        flex-direction: column;
        justify-content: center;
        height: 100%;
    }
    .controls {
        position: absolute;
        top: 50%;
        border: 2px solid var(--primary-dark);
        padding: 10px;
    }
    .controls:before, .exit:before {
        display: none;
    }
    .controls.prev {
        left: 0;
    }
    .controls.next {
        right: 0;
    }
    .exit {
        border: 2px solid var(--primary-dark);
        padding: 10px;
        display: inline-block;
        margin: 40px auto 0;
    }
</style>