<script lang='ts'>
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';
	import { goto } from '$app/navigation'
	import { encodeHexLowerCase } from '@oslojs/encoding';

	let { form }: { form: ActionData } = $props();
</script>


<section class="h-screen m-14 flex flex-col items-center">
	<p style='color: red'>{form?.message ?? ''}</p>	

	<div class="card preset-filled-surface-100-900 p-4 rounded-xl">
		<h1 class="text-center h2">Create an account</h1>
	
		<form method="get" class="text-center mt-6" use:enhance action='?/register'>
			<label for="username">Username: </label>
			<input type="text" name="username" id="username" class="text-black" /> <br />
			<label for="password">Password: </label>
			<input type="password" name="password" id="password" class="text-black mt-2.5" /> <br />
			<input type="submit" class="btn variant-filled-primary mt-5" value="Create"/>
			<!-- <a href="/start" class="btn variant-filled-primary mt-5">Sign In</a> -->
	
		</form>
		<a href="/login" class="btn variant-filled-secondary mt-5 text-center ml-3">I already have an account</a>
	
	</div>

</section>



