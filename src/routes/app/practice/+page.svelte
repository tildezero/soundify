<script>
	import { goto } from '$app/navigation';
	
	import { Music } from '@lucide/svelte';
	import { enhance } from '$app/forms';
	import { Avatar, ProgressRing, Segment, Slider, Switch } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';


	// import Camera from './Camera.svelte'
	
	let iconClass = $state(['badge-icon', 'w-20', 'h-20', 'preset-filled-primary-500'])

	let cameraOn = $state(false);

	function changeColor() {
		if (iconClass.includes('preset-filled-primary-50-950')) {
			iconClass.pop();
			iconClass.push('preset-filled-error-50-950');
		} else {
			iconClass.pop();
			iconClass.push('preset-filled-primary-50-950');
		}
	}

	window.onmessage = (event) => {
		if (event.data.startsWith('success')) {
			alert(`result recieved! accuracy=${event.data.split(" ").at(1)}`)
		}
	}


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
	<span class={iconClass.join(" ")}>
		<Music size={48} />
	</span>
	<div>
		<button class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3" onclick={() => cameraOn = true}>Begin exercise →</button>
		{#if cameraOn} 
			<div style="position: relative;">
				<canvas class="output_canvas" id="output_canvas" style="position: absolute; left: 0px; top: 0px;"></canvas>
			</div>

			<!-- <Camera /> -->
		{/if}
		<button onclick={() => goto('/app/practice/settings')} class="btn t preset-filled mt-10 text-m font-bold text-center ">⚙</button>
	</div>
</section>


