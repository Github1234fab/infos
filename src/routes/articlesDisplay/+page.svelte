<script>
	import { onMount } from 'svelte';
	import Article from '../../Components/Article.svelte';
	let query = '';
	let articles = [];

	function handleSubmit() {
		fetchArticles();
	}

	const fetchArticles = async () => {
		const url = `https://newsapi.org/v2/everything?q=${query}&apiKey=0e801b68d50641ac940d8d3442dbfaac`;
		const response = await fetch(url);
		const data = await response.json();
		articles = data.articles;
		articles.sort((a, b) => new Date(b.publishedAt) - new Date(a.publishedAt));
		console.log(articles);
	};
</script>

<main>
    <form action="">
        <label for="any">Recherchez vos articles en tapant des mots clefs, des expressions, la date du jour, etc. <br>
     Pour traduire les résultats dans votre langue, utilisez une extension de votre navigateur. </label>
	<input bind:value={query} name="any"type="text" placeholder="Search" />
	<button on:click={handleSubmit}>Rechercher</button>
    <input type= "reset" value="Effacer">
</form>
	<div class="container">
		{#each articles as article}
			<Article {article} />
		{/each}
	</div>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 20px;
		padding: 20px;
	}
    form {  
        display: flex; 
        flex-direction: column; 
        gap: 10px;
    }
    label {
        text-align: center;
        font-size: 1rem;
        color: grey;
    }
	input {
		padding: 10px 30px;
		text-align: left;
		width: 60%;
		margin: 0 auto;
	}
	input::placeholder{
		text-align: center;
	}
    input[type=reset] {
        padding: 5px 10px;
        text-align: center;
        cursor: pointer;
        transition: 0.3s ease-in-out;
        width: 30%;
        margin: 0 auto;
    }
	button {
		padding: 5px 10px;
		cursor: pointer;
		transition: 0.3s ease-in-out;
        width: 30%;
        margin: 0 auto;
	}
	button:hover {
		background-color: #262525;
		color: white;
	}
    button:active {
		background-color: #262525;
		color: white;
        transition: 0s;
	}

	.container {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-wrap: wrap;
		width: 100%;
		height: auto;
		gap: 20px;
		padding: 20px;
	}

    @media (max-width: 768px) {
    .container {
       padding: 5px;
    }
    button{
        width: 40%;
    }
    input[type=reset] {
        width: 40%;
    }
}

</style>
