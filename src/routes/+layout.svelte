<script lang="ts">
	import '../app.css';
	let { children } = $props();

	import { goto } from '$app/navigation';
	import { Avatar, ProgressRing, Segment, Slider, Switch } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	const previewCardClasses = 'card bg-noise bg-surface-50-950 border-[1px] border-surface-200-800 flex justify-center items-center p-8';

	let color = $state('#bada55');
</script>

<header class="sticky top-0 z-50 bg-surface-50-950 shadow-xl">
	<div class="container mx-auto grid grid-cols-[auto_1fr_auto] items-center gap-10 p-4">
		<h1 class="h3">Soundify</h1>
		<p class="text-xs opacity-60 collapse md:visible">Sightreading made easy.</p>
		<button onclick={() => goto('/login')} class="btn preset-filled">Log In</button>
	</div>
</header>


<!-- {@render children()} -->

<slot />


