<script>
  import { count } from '../scripts/stores.svelte';
  let slide = 1;
  count.subscribe(n => slide = n);
</script>
<nav>
  <div class="container">
    <span id="brand"><a href="/"><img alt="planarian" src="/logo.svg" />Home</a></span>
    <a href="/about">About</a>&nbsp;
    <a href="/contact">Contact</a>&nbsp;
    <a href="/slides/{slide}">Slides</a>
  </div>
</nav>

<style>
  nav, .container, #brand, #brand a {
    display: flex;
  }
  nav {
    min-height: 60px;
    box-shadow: 0px 2px 3px var(--base);
  }
  #brand {
    flex: 1;
  }
  a {
    align-self: center;
    align-items: center;
    color: var(--base-dark);
    text-decoration: none;
  }
  img {
    margin-right: 10px;
  }
</style>
