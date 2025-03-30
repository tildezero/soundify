<script lang="ts">
	import type { HandLandmarkerResult } from '@mediapipe/tasks-vision';
	import WebcamVideo from '$lib/WebcamVideo.svelte';
	import { startRecognition } from '$lib/recognizer';

	let videoElem: HTMLVideoElement | undefined = $state(undefined);
	let buttonElem: HTMLButtonElement | undefined = $state(undefined);
	let isWebcamEnabled = $state(false);

	// $: if (isWebcamEnabled) {
	// 	startRecognition(videoElem, processResult);
	// 	buttonElem.disabled = true;
	// 	//buttonElem.style.display = 'none'; // 有効化したらボタンを消す
	// }

	$effect(() => {
		if (isWebcamEnabled) {
			console.log('webcam is enabled');
			if (videoElem) {
				startRecognition(videoElem, processResult);
			}
			if (buttonElem) {
				buttonElem.disabled = true;
			}
			//buttonElem.style.display = 'none'; // 有効化したらボタンを消す
		}
	});

	let categoryName1: string = '?'; // 1 つ目の手の形状（カテゴリ）
	let categoryName2: string = '?'; // 2 つ目の手の形状（カテゴリ）
	let score1 = 0.0; // 1 つ目のカテゴリのスコア
	let score2 = 0.0; // 2 つ目のカテゴリのスコア

	function processResult(result: GestureRecognizerResult) {
		const category1 = result.gestures.at(0)?.at(0);
		const category2 = result.gestures.at(1)?.at(0);
		categoryName1 = category1?.categoryName ?? '?';
		categoryName2 = category2?.categoryName ?? '?';
		score1 = category1?.score ?? 0.0;
		score2 = category2?.score ?? 0.0;
	}
</script>

<div>
	<WebcamVideo bind:videoElem active={isWebcamEnabled} />
</div>
<button
	class="btn preset-filled-primary-50-950"
	bind:this={buttonElem}
	onclick={() => (isWebcamEnabled = true)}>Enable webcam</button
>

<p>c1: {categoryName1}</p>
<p>c2: {categoryName2}</p>