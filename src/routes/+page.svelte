<main>
	<div class="wrapper__text">
		<div class="wrapper__h1">
			<h1>News <span>Detox</span></h1>
		</div>
		<h2>Vous souhaitez <br />reprendre la main <br />sur le fil d'info ?</h2>
		<a href="/testGps">Accès</a>
	</div>
</main>

<style>
	main {
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		/* background-image: url('https://images.pexels.com/photos/167538/pexels-photo-167538.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'); */
        background-image: url("https://images.pexels.com/photos/33153/raisting-sattelit-reception-signal.jpg");
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		background-color: #4d4e47;
	}
	.wrapper__text {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 30px;
		padding: 40px;
		color: white;
		background-color: rgba(0, 0, 0, 0.66);
		padding: 20px;
	}
	.wrapper__text h1 span {
		font-size: 3rem;
		text-transform: uppercase;
		letter-spacing: -0.9px;
		background-color: white;
		color: black;
		padding: 5px;
		font-weight: 900;
        text-align: center;
	}
	.wrapper__h1 {
		border: 1px solid white;
		width: 70%;
        letter-spacing: -2px;
	}
	.wrapper__text h1 {
		font-size: 4rem;
		text-align: center;
		line-height: 36px;
		margin-top: 15px;
	}
	.wrapper__text h2 {
		font-size: 2rem;
		font-weight: 400;
		text-align: center;
		line-height: 30px;
	}

	a {
		text-decoration: none;
		padding: 20px 30px;
		border: 1px solid grey;
		border-radius: 5px;
		background-color: black;
		color: beige;
		font-size: 1rem;
	}
	a:hover {
		background-color: beige;
		color: black;
	}
	a:active {
		background-color: beige;
		color: black;
	}
	@media screen and (max-width: 768px) {
		.wrapper__text {
			padding: 10px;
			width: 80%;
		}
		.wrapper__text h1 {
			font-size: 3rem;
			text-transform: uppercase;
			letter-spacing: -0.9px;
		}
		.wrapper__text h1 span {
			font-size: 3rem;
			text-transform: uppercase;
			letter-spacing: -0.9px;
			background-color: white;
			color: black;
			padding: 5px;
		}
		.wrapper__text h2 {
			font-size: 1.2rem;
		}

		a {
			padding: 10px 20px;
			font-size: 1rem;
		}
	}
</style>
