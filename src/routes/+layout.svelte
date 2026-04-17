<script lang="ts">
	import { AppBar } from '@skeletonlabs/skeleton-svelte';
	import '../routes/layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<title>Mykola Kikets | Portfolio</title>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="h-screen flex flex-col bg-surface-950 text-surface-50 overflow-hidden">
	<!-- Fixed Header -->
	<div class="fixed top-0 w-full z-50 bg-surface-950/80 backdrop-blur-md border-b border-surface-800">
		<AppBar>
			{#snippet lead()}
				<strong class="text-xl uppercase tracking-widest px-4">Mykola Kikets</strong>
			{/snippet}
			{#snippet trail()}
				<div class="flex items-center gap-6 px-4">
					<a href="#hero" class="hover:text-primary-400 transition-colors text-sm uppercase tracking-wider">Home</a>
					<a href="#about" class="hover:text-primary-400 transition-colors text-sm uppercase tracking-wider">About</a>
					<a href="#projects" class="hover:text-primary-400 transition-colors text-sm uppercase tracking-wider">Projects</a>
					<a href="#experience" class="hover:text-primary-400 transition-colors text-sm uppercase tracking-wider">Experience</a>
					<a href="https://github.com/mkikets99" target="_blank" rel="noreferrer" class="btn bg-surface-800 hover:bg-surface-700 py-1.5 px-4 rounded text-xs uppercase font-bold">
						GitHub
					</a>
				</div>
			{/snippet}
		</AppBar>
	</div>

	<!-- Scroll Snapping Container -->
	<main class="flex-1 overflow-y-auto scroll-smooth snap-y snap-mandatory outline-none">
		{@render children()}
		
		<!-- Footer as a small snap section or attached to the last one -->
		<footer class="snap-start h-20 flex items-center justify-center text-surface-400 text-xs border-t border-surface-800 bg-surface-950">
			&copy; {new Date().getFullYear()} Mykola Kikets. "when curiosity leads the way"
		</footer>
	</main>
</div>

<style>
	:global(html, body) {
		@apply h-full overflow-hidden antialiased;
		scroll-behavior: smooth;
	}

	/* Hide scrollbar for a cleaner modular look */
	main::-webkit-scrollbar {
		display: none;
	}
	main {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}
</style>
