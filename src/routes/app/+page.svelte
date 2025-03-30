<script lang="ts">
	import { goto } from '$app/navigation';
	import { Avatar, ProgressRing, Segment, Slider, Switch, Progress } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	

	let color = $state('#bada55');
	// let { name="John", accuracyPercentage=0, lessonsCompleted=13 } = $props();
	import type { PageServerData } from './$types';

	let { data }: { data: PageServerData } = $props();

	let goodName = data.user.username.charAt(0).toUpperCase() + data.user.username.slice(1)
</script>

<main class="container mx-auto space-y-4 px-4 py-12">
	<!-- -------------------------------------------------------- -->
	<header class={headerClasses}>
		<h1 class="h1">Welcome, {goodName}! </h1>
	</header>
	<p class="p text-left ">Get ready to learn, {goodName}! Your rhythmic journey is on its course! Let's hit 20 exercises!</p>
	<!-- -------------------------------------------------------- -->
	<section class="items-left flex flex-col">
		<header class={headerClasses}>
			<h4 class="h4">Stats: </h4>
		</header>
	</section>

	<div class="flex w-full flex-col gap-2">

		<p class="p max-w-prose">Average accuracy: {data.user.avgAccuracy}%</p>
		<Progress value={data.user.avgAccuracy ?? 0 * 100} max={100} meterBg="bg-tertiary-500" />
	</div>
	<div class="flex w-full flex-col gap-2">

		<p class="p max-w-prose">Lessons completed: {data.user.sessionsCompleted}/20</p>
		<Progress value={data.user.sessionsCompleted} max={20} meterBg="bg-tertiary-500" />
	</div>

	<section class="items-left flex flex-col">
		<header class={headerClasses}>
			<h4 class="h4">Engage: </h4>
		</header>
	</section>
	<section class="items-center flex flex-col">
	
    <!--bar crap would go here -->
	<button onclick={() =>  goto('/app/practice')} class="btn t preset-filled mt-5 text-m font-bold text-center p-x-5 p-y-3">Practice →</button>
	<button onclick={() =>  goto('/app/learn')} class="btn t preset-filled mt-5 text-m font-bold text-center p-x-5 p-y-3">Learn →</button>
</section>

</main>
