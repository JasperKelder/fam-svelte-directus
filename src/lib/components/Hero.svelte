<script>
	import { getAssetURL } from '$lib/get-asset-url';
	export let article;
</script>

<article class="hero">
	<div class="hero__topWrapper">
		<div class="hero__imageWrapper">
			<img src={getAssetURL(article.cover_image)} alt="" loading="lazy" />
		</div>
	</div>
	<h1 class="hero__title">
		<a href={`/articles/${article.id}`}>{article.title}</a>
	</h1>
	<p class="hero__excerpt">{article.excerpt}</p>
	<div class="hero__detail">
		<div class="hero__detailAuthorImage">
			<img src={getAssetURL(article.author.avatar)} alt="" loading="lazy" />
		</div>
		<div>
			<div class="hero__detailAuthorName">
				{`${article.author.first_name} ${article.author.last_name}`}
			</div>
			<div>{article.publish_date}</div>
		</div>
	</div>
</article>

<style>
	.hero {
		margin-bottom: 16px;
		padding-bottom: 32px;
		border: 0 solid var(--background-accent);
		border-bottom-width: 1px;
	}

	@media (min-width: 640px) {
		.hero {
			margin-bottom: 32px;
		}
	}

	.hero__topWrapper,
	.hero__title,
	.hero__detail {
		margin-bottom: 16px;
	}

	.hero__topWrapper {
		position: relative;
	}

	.hero__imageWrapper {
		position: relative;
		padding-bottom: calc(8 / 16 * 100%);
		overflow: hidden;
		background-color: var(--background-accent);
	}

	.hero__imageWrapper img {
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.hero__title a:hover {
		color: var(--orange);
		transition: color 0.4s;
	}
</style>
