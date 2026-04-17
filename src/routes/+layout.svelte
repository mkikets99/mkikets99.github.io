<script lang="ts">
	import { AppBar } from '@skeletonlabs/skeleton-svelte';
	import '../routes/layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<title>M. Kikets | Portfolio</title>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="h-full grid grid-rows-[auto_1fr_auto] bg-surface-950 text-surface-50">
	<!-- Header -->
	<AppBar>
		{#snippet lead()}
			<strong class="text-xl uppercase">M. Kikets</strong>
		{/snippet}
		{#snippet trail()}
			<div class="flex items-center gap-4">
				<a href="#about" class="hover:underline">About</a>
				<a href="#projects" class="hover:underline">Projects</a>
				<a href="#experience" class="hover:underline">Experience</a>
				<a href="https://github.com/mkikets99" target="_blank" rel="noreferrer" class="btn bg-surface-800 hover:bg-surface-700">
					GitHub
				</a>
			</div>
		{/snippet}
	</AppBar>

	<!-- Main Content -->
	<main class="container mx-auto p-8 space-y-16 overflow-y-auto">
		{@render children()}
	</main>

	<!-- Footer -->
	<footer class="p-8 text-center text-surface-400 text-sm border-t border-surface-800">
		&copy; {new Date().getFullYear()} M. Kikets. Built with SvelteKit & Skeleton UI.
	</footer>
</div>

<style>
	:global(html, body) {
		@apply h-full overflow-hidden;
	}
</style>
