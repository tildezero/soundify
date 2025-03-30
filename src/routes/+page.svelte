<script>
	import { goto } from '$app/navigation';
</script>


<section class="h-screen items-center flex flex-col">
	<h2 class="h2 mt-14 font-bold text-center">Learn sightreading!</h2>
	<p class="p mt-5 text-center max-w-prose">An engaging, kid-friendly, CV-powered way for young children to enrich their rhythmic abilities.</p>
	<button onclick={() =>  goto('/register')} class="btn t preset-filled mt-10 text-m font-bold text-center p-x-5 p-y-3">Get Started →</button>
</section>
