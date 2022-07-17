<script>
	import { getAssetURL } from '$lib/get-asset-url';
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
