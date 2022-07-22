<script context="module">
	import { getDirectusClient } from '$lib/client';
	import { formatRelativeTime } from '$lib/format-relative-time';

	export const load = async () => {
		const directus = await getDirectusClient();

		let response;
		try {
			response = await directus.items('articles').readByQuery({
				fields: ['*', 'author.avatar', 'author.first_name', 'author.last_name'],
				sort: '-publish_date'
			});
		} catch (err) {
			return {
				status: 404
			};
		}

		const formattedArticles = response.data.map((article) => {
			return {
				...article,
				publish_date: formatRelativeTime(new Date(article.publish_date))
			};
		});

		if (!formattedArticles) {
			return {
				status: 404
			};
		}

		const [hero, ...articles] = formattedArticles;

		return {
			props: {
				hero,
				articles
			}
		};
	};
</script>

<script>
	import Hero from '$lib/components/Hero.svelte';
	import Article from '$lib/components/Article.svelte';

	export let hero, articles;
</script>

<svelte:head>
	<title>Blog - Fundament All Media</title>
</svelte:head>

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

<style>
	.main-content {
		margin-top: 12rem;
	}
</style>
