<script>
	import { page } from '$app/stores';
</script>

<header>
	<div>
		<a sveltekit:prefetch href="/" class:active={$page.url.pathname === '/'}>
			<img id="logo" width="208.659" height="15.297" src="logo.png" alt="Fundament All Media" />
		</a>
	</div>

	<nav>
		<ul>
			<li id="home">
				<a sveltekit:prefetch href="/" class:active={$page.url.pathname === '/'}>Fundament</a>
			</li>
			<li>
				<a sveltekit:prefetch href="/articles" class:active={$page.url.pathname === '/articles'}
					>Blog</a
				>
			</li>
			<li>
				<a sveltekit:prefetch href="/portfolio" class:active={$page.url.pathname === '/portfolio'}
					>Portfolio</a
				>
			</li>
			<li>
				<a sveltekit:prefetch href="/team" class:active={$page.url.pathname === '/team'}>Team</a>
			</li>
			<li>
				<a sveltekit:prefetch href="/contact" class:active={$page.url.pathname === '/contact'}
					>Contact</a
				>
			</li>
		</ul>
	</nav>
</header>

<style>
	header {
		top: 0;
		display: flex;
		align-items: center;
		height: 84px;
		vertical-align: center;
		position: fixed;
		width: 100vw;
		z-index: 2;
		background-color: var(--white);
		border-bottom: 0.2rem solid var(--orange);
	}

	nav {
		margin-left: auto;
		margin-right: 25px;
	}

	li {
		display: inline-block;
	}

	a {
		text-decoration: none;
		color: var(--black);
		text-transform: uppercase;
		font-size: 14px;
		font-weight: 300;
		margin-right: 15px;
	}

	img {
		height: 15.3px;
		margin-left: 25px;
	}

	.active {
		font-weight: 700;
	}

	nav a {
		display: block;
		position: relative;
		padding: 8px 0;
	}

	nav a::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 2px;
		background-color: var(--orange);
		opacity: 0;
		transition: opacity 300ms, transform 300ms;
	}

	@media (hover: hover) {
		nav a:hover::after,
		nav a:focus::after {
			opacity: 1;
			transform: translate3d(0, 2px, 0);
		}

		nav li a::after {
			opacity: 1;
			transform: scale(0);
			transform-origin: center;
		}

		nav li a:hover::after,
		nav li a:focus::after {
			transform: scale(1);
		}
	}

	@media only screen and (min-width: 575px) {
		#home {
			display: none;
		}
	}

	@media only screen and (max-width: 575px) {
		#logo {
			display: none;
		}

		nav {
			margin: auto;
		}
	}

	@media only screen and (max-width: 425px) {
		a {
			font-size: 1.5rem;
			margin-right: 0.5rem;
		}
	}

	@media only screen and (max-width: 380px) {
		a {
			font-size: 1.4rem;
		}
	}
</style>
