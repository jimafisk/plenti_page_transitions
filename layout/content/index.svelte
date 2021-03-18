<script>
	export let title, intro, components, content, allContent;
	import Grid from '../components/grid.svelte';
	import Uses from "../components/source.svelte";
	import Pager from "../components/pager.svelte";
  import { slide } from "svelte/transition";

	$: currentPage = content.pager;
	let postsPerPage = 3;
	let allPosts = allContent.filter(content => content.type == "blog");
	let totalPosts = allPosts.length;
	let totalPages = Math.ceil(totalPosts / postsPerPage);
	$: postRangeHigh = currentPage * postsPerPage;
	$: postRangeLow = postRangeHigh - postsPerPage;
</script>

<div in:slide={{ delay: 300 }} out:slide={{ delay: 300}}>
<h1>{title}</h1>

<section id="intro">
	{#each intro as paragraph}
		<p>{@html paragraph}</p>
	{/each}
</section>

<div>
	<h3>Recent blog posts:</h3>
	<Grid items={allPosts} {postRangeLow} {postRangeHigh} />
	<br />
</div>
<Pager {currentPage} {totalPages} />

<Uses {content} />
</div>