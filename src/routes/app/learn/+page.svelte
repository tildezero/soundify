<script>
	import { goto } from '$app/navigation';
	import { Avatar, ProgressRing, Segment, Slider, Switch } from '@skeletonlabs/skeleton-svelte';

	// Common Class Lists
	const headerClasses = 'space-y-2 pb-2 border-b-2 border-surface-800-200';
	

	let color = $state('#bada55');
</script>

<main class="container mx-auto px-4 py-20">
	<!-- -------------------------------------------------------- -->
	<header class={headerClasses}>
		<h2 class="h2">Learn </h2>
	</header>
	<!-- -------------------------------------------------------- -->
	<h4 class="h4 text-left mt-10">How does it work? </h4>
	<p class="p text-left mt-5">First, you put your hands in frame of the webcam. In time with the beat, you want to pinch your pointer and thumb fingers together when the sliding red cursor is in a black region. You want to then open those fingers together when the cursor is in a blue region. Your score is based on how accurately in time your pinch and relase motions are!</p>
	<section class="mt-5 items-center flex flex-col">
		<img class="h-auto max-w-full bg-surface-500 rounded-container" src="https://grammarpartyblog.com/wp-content/uploads/2013/01/ok_hand.jpg?w=640" />
	</section>
	<h4 class="h4 text-left mt-10">Who can use this? </h4>
	<p class="p text-left mt-5">The mechanics are simple and desgined for kids! The pinch motions are simple; all you need is a working webcam and speaker to hear the metronome.</p>
</main>


<section class="h-screen items-center flex flex-col">
    <img class="h-auto max-w-full bg-surface-500 rounded-container" src="https://media.istockphoto.com/id/1010535774/photo/preschool-childs.jpg?s=612x612&w=0&k=20&c=Kgv_6XuoSgl7sM9AaCbGZ1rhPT8A1AOu-NRhGwRf6XQ=" />
</section>