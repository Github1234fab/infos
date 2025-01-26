<script>
	export let article;
</script>

<div class="article">
	<img src={article.urlToImage} alt={article.title} />
	<h1>{article.title}</h1>
	<p>{article.description}</p>
	<a href={article.url} target="_blank">Read more</a>
	<div class="wrapper__info">
	<p><span>Published at:</span> {article.publishedAt}</p>
	<p><span>Author: </span> {article.author}</p>
	<p><span>Source: </span> {article.source.name}</p>
</div>
</div>

<style>
	.article {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.25);
		padding: 20px;
		gap: 20px;
		margin-bottom: 10px;
		flex-grow: 1;
		width: 300px;
		height: 680px;
		overflow: hidden;
	}
	.wrapper__info {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: flex-start;
		gap: 0px;
	}
	.article p {
		font-size: 1rem;
		text-align: left;
		line-height: 24px;
		width: 100%;
	}

	.article h1 {
		font-size: 1.5rem;
		text-align: left;
		line-height: 24px;
		width: 100%;
	}
	
	img {
		max-width: 100%;
		max-height: 250px;
	}
	span {
		font-weight: bold;
	}

@media (max-width: 768px) {
    .article {
       height: auto;
    }

}
</style>
