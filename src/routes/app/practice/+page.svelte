<script>
	import { goto } from '$app/navigation';
	import { Heart } from '@lucide/svelte';
	import { enhance } from '$app/forms';
	import { Avatar, ProgressRing, Segment, Slider, Switch } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	



</script>

<main class="container mx-auto space-y-20 px-4 py-20">
	<!-- -------------------------------------------------------- -->
	<header class={headerClasses}>
		<h2 class="h2">Practice </h2>
	</header>
	<!-- -------------------------------------------------------- -->

</main>
<section class="h-screen items-center flex flex-col">
    <!--bar crap would go here -->
	
	<div>
		<button class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3">Begin exercise →</button>
		<button onclick={() => goto('/app/practice/settings')} class="btn t preset-filled mt-10 text-m font-bold text-center ">⚙</button>
	</div>
</section>


