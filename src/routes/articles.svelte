<script>
	import Hero from '$lib/components/Hero.svelte';
	import Article from '$lib/components/Article.svelte';

	export let hero, articles;
</script>

<svelte:head>
	<title>Blog - Fundament All Media</title>
</svelte:head>

<main>
	<section class="main-content">
		<div class="container">
			<Hero article={hero} />
			<div class="articles-grid">
				{#each articles as article, index}
					<Article {article} bordered={index !== articles.length - 1} />
				{/each}
			</div>
		</div>
	</section>
</main>
