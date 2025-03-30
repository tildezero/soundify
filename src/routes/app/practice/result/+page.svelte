<script>
	import { goto } from '$app/navigation';
    
	import { Avatar, ProgressRing, Segment, Slider, Switch, Progress } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	

	let color = $state('#bada55');
    let { accuracyPercentage = 87} = $props();
</script>

<main class="container mx-auto space-y-20 px-4 py-20">
	<!-- -------------------------------------------------------- -->
	<header class={headerClasses}>
		<h2 class="h2">Practice </h2>
	</header>
	<!-- -------------------------------------------------------- -->
    <section class="items-center flex flex-col">
        <h3 class="h3">Your results: </h3>
        <!--bar crap would go here -->
        <div class="flex w-full flex-col gap-2">
            <p class="p max-w-prose">Accuracy: {accuracyPercentage}%</p>
            <Progress value={accuracyPercentage} max={100} meterBg="bg-tertiary-500" />
        </div>
        
        <h3 class="h5 mt-10">Great job!</h3>
        <button onclick={ () => goto('/app/practice')} class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3">New exercise →</button>
        <button onclick={ () => goto('/app')} class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3">Return →</button>
    </section>

</main>

