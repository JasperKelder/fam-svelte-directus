<script context="module">
	import { getDirectusClient } from '$lib/client';
	import { formatRelativeTime } from '$lib/format-relative-time';
	import { getAssetURL } from '$lib/get-asset-url';

	export const load = async ({ params }) => {
		const { id } = params;

		const directus = await getDirectusClient();

		let article;
		try {
			article = await directus.items('articles').readOne(id, {
				fields: ['*', 'author.avatar', 'author.first_name', 'author.last_name']
			});
		} catch (err) {
			return {
				status: 404
			};
		}

		const formattedArticle = {
			...article,
			publish_date: formatRelativeTime(new Date(article.publish_date))
		};

		const moreArticlesResponse = await directus.items('articles').readByQuery({
			fields: ['*', 'author.avatar', 'author.first_name', 'author.last_name'],
			filter: {
				_and: [{ id: { _neq: article.id } }, { status: { _eq: 'published' } }]
			},
			limit: 2
		});
		const formattedMoreArticles = moreArticlesResponse.data.map((moreArticle) => {
			return {
				...moreArticle,
				publish_date: formatRelativeTime(new Date(moreArticle.publish_date))
			};
		});

		return {
			props: { article: formattedArticle, moreArticles: formattedMoreArticles }
		};
	};
</script>

<script>
	import MoreArticles from '$lib/components/MoreArticles.svelte';

	export let article, moreArticles;
</script>

<div class="current-article">
	<section>
		<div class="container">
			<h1 class="current-article__title">{article.title}</h1>
			<div class="current-article__detail">
				<div class="current-article__wrapperOuter">
					<div class="current-article__wrapperInner">
						<div class="current-article__authorImage">
							<img src={getAssetURL(article.author.avatar)} alt="" loading="lazy" />
						</div>
						<div>
							<div class="current-article__authorName">
								{`${article.author.first_name} ${article.author.last_name}`}
							</div>
							<div class="current-article__time">
								{article.publish_date}
							</div>
						</div>
					</div>
				</div>
				<div class="current-article_coverImage">
					<img src={getAssetURL(article.cover_image)} alt="" />
				</div>
			</div>
			<div class="current-article__body">
				<div class="current-article__bodyContent">{@html article.body}</div>
			</div>
		</div>
	</section>
	<MoreArticles articles={moreArticles} />
</div>

<style>
	.current-article {
		margin-top: 11rem;
	}
</style>
