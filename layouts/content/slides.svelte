<script>
  export let title, description, order, content;
  import { scale } from "svelte/transition";
  import { count } from '../scripts/stores.svelte';
  function setCount(n) {
    count.set(n);
  }
</script>

<a on:click={() => setCount(Number(order)-1)} class="controls prev" href="/slides/{Number(order)-1}">Previous</a>

{#key content}  
<div id="slides" in:scale={{ delay: 300 }} out:scale>
    <div id="slide-wrapper">
        <h1>{order}: {title}</h1>
        <div>
        {#each description as paragraph}
            <p>{@html paragraph}</p>
        {/each}
        </div>
    </div>
    <a class="exit" href="/">Exit Slides</a>
</div>
{/key}

<a on:click={() => setCount(Number(order)+1)} class="controls next" href="/slides/{Number(order)+1}">Next</a>

<style>
    #slide-wrapper {
        background-color: var(--base-dark);
        color: var(--base);
        padding: 20px 20px 40px;
    }
    #slides {
        display: flex;
        flex-direction: column;
        justify-content: center;
        height: 100%;
    }
    .controls {
        position: absolute;
        margin: 20px;
        top: 50%;
    }
    .controls.prev {
        left: 0;
    }
    .controls.next {
        right: 0;
    }
    .exit {
        display: inline-block;
        margin: 40px auto 0;
    }
</style>