<script context="module">
	/** @type {import('@sveltejs/kit').Load} */
	export const load = async ({ url: { pathname } }) => ({
		props: { pathname }
	});
</script>

<script>
	import Header from '$lib/components/Header.svelte';
	import '../app.css';
	import '../main.css';
	import PageTransition from '$lib/components/PageTransition.svelte';
	export let pathname;
</script>

<Header />
<PageTransition {pathname}>
	<slot />
</PageTransition>
