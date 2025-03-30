<script>
	import { goto } from '$app/navigation';
	import { Avatar, ProgressRing, Segment, Slider, Switch } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	

	let color = $state('#bada55');
</script>

<main class="container mx-auto space-y-20 px-4 py-20 items-center">
	<!-- -------------------------------------------------------- -->
		<h3 class="h3 text-center">Settings: </h3>
	<!-- -------------------------------------------------------- -->

</main>
<section class="h-screen items-center flex flex-col">
    <!--bar crap would go here -->
	<button onclick={() => goto('/app/practice')} class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3">Return →</button>
</section>
