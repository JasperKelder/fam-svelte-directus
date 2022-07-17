<svelte:head>
	<title>Fundament All Media</title>
</svelte:head>

<section>
	<div class="overlay">
		<div class="content verbinding">
			<h1 id="verbinding">
				<span>Maak de</span>
				<span>verbinding</span>
			</h1>
			<p>Kijk hoe wij jullie wereld kunnen veranderen met onze online of offline mogelijkheden</p>
			<a class="button" href="#style">Bekijk meer</a>
		</div>
	</div>
</section>

<section id="style">
	<div class="content">
		<h2>
			<span>Leveren in</span>
			<span>Style</span>
		</h2>
		<div class="flex">
			<img id="bakfiets_image" src="/bakfiets.png" alt="Klanten" />
		</div>
		<a class="button" href="#concept">Bekijk meer</a>
	</div>
</section>

<section id="concept">
	<div class="content">
		<h2>
			<span>Een goed</span>
			<span>Concept</span>
		</h2>
		<div class="flex">
			<img id="lamp_image" src="/lamp.png" alt="Concept" />
		</div>
		<a class="button" href="#design">Bekijk meer</a>
	</div>
</section>

<section id="design">
	<div class="content">
		<h2>
			<span>Maak een mooi</span>
			<span>Design</span>
		</h2>
		<div class="flex">
			<img id="feather_image" src="/feather.png" alt="Design" />
		</div>
		<a class="button" href="#techniek">Bekijk meer</a>
	</div>
</section>

<section id="techniek">
	<div class="content">
		<h2>
			<span>Verbind de juiste</span>
			<span>Techniek</span>
		</h2>
		<div class="flex">
			<img id="techniek_image" src="/propeller.png" alt="Techniek" />
		</div>
		<a class="button" href="#persoonlijk">Bekijk meer</a>
	</div>
</section>

<section id="persoonlijk">
	<div class="content">
		<h2>
			<span>Maak het</span>
			<span id="persoonlijk_title">Persoonlijk</span>
		</h2>
		<div class="flex">
			<img id="coffe_image" src="/coffee.png" alt="Contact" />
		</div>
		<a class="button" href="/articles">Lees onze blog</a>
	</div>
</section>

<style>
	section {
		height: 100vh;
	}

	section:nth-of-type(1) {
		background-image: url('/computer.jpg');
		background-size: cover;
		background-position: 50%;
	}

	section:nth-of-type(2) {
		background-color: rgb(198, 82, 82);
	}

	section:nth-of-type(3) {
		background-color: rgb(82, 194, 189);
	}

	section:nth-of-type(4) {
		background-color: rgb(98, 63, 117);
	}

	section:nth-of-type(5) {
		background-color: rgb(87, 188, 144);
	}

	section:nth-of-type(6) {
		background-color: rgb(69, 148, 225);
	}

	.overlay {
		height: 100%;
		background-color: rgba(0, 0, 0, 0.35);
		display: flex;
		justify-content: center;
	}

	.content {
		position: relative;
		top: 12%;
	}

	.content > h1 > span,
	.content > h2 > span {
		display: flex;
		justify-content: center;
		color: white;
	}

	.content.verbinding > h1 > span {
		font-family: 'Pacifico';
		font-size: 88px;
		line-height: 100px;
		font-weight: 400;
	}

	.content > h2 > span:nth-child(2) {
		font-family: 'Pacifico';
		font-size: 88px;
		font-weight: 400;
		color: black;
	}

	.content p {
		margin-top: 30px;
		color: white;
		font-size: 24px;
		font-weight: 300;
		max-width: 500px;
		text-align: center;
	}

	.content a {
		text-transform: uppercase;
		text-decoration: none;
		background-color: rgb(255, 255, 255);
		border-radius: 50px;
		padding: 8px 16px;
		border: 1px solid black;
		color: black;
		position: absolute;
		margin-top: 50px;
		left: 50%;
		transform: translate(-50%);
		top: 55rem;
	}

	@media only screen and (max-height: 720px) {
		.content a {
			top: 35rem;
		}
	}

	.flex {
		display: flex;
		justify-content: center;
	}

	.button {
		transition: color 0.4s;
	}

	.button:hover {
		color: var(--orange);
	}

	#verbinding {
		margin-top: 4rem;
	}

	@media only screen and (max-width: 500px) {
		#verbinding span {
			font-size: 6rem;
			line-height: 7rem;
		}

		#bakfiets_image {
			position: absolute;
			top: 15rem;
			width: 110%;
		}

		#persoonlijk_title {
			font-size: 7.5rem;
		}
	}
</style>
