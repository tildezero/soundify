<script lang="ts">
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';
	import { goto } from '$app/navigation';
	import { encodeHexLowerCase } from '@oslojs/encoding';

	let { form }: { form: ActionData } = $props();
</script>

<section class="m-14 flex h-screen flex-col items-center">

	<div class="card preset-filled-surface-100-900 rounded-xl p-4 m-5 space-y-5">
		<h2 class="text-center h2">Create an account</h2>
		<form method="post" use:enhance action="?/register">
			<label class="label">
				<span class="label-text">Username</span>
				<input class="input" type="text" placeholder="Username" name="username" id="username" />
			</label>
		
			<label class="label">
				<span class="label-text">Password</span>
				<input class="input" type="password" placeholder="Password" name="password" id="password" />
			</label>

			<label class="label"> 
				<span class="label-text">&nbsp;</span>
				<input class="input btn preset-tonal-success" type="submit" value="Create" />
			</label>
		</form>

		<button onclick={() => goto('/login')} class="btn preset-filled mx-auto block">Already have an account?</button>


		<p style="color: red">{form?.message ?? ''}</p>
	</div>
</section>
