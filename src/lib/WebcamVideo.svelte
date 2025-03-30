<script lang="ts">
	/** Webcam による映像キャプチャを開始するためのフラグ */
	export let active: boolean = false;

	/** video 要素の bind 用 */
	export let videoElem: HTMLVideoElement | undefined;

	$: if (active) {
		startCapture();
	}

	const hasGetUserMedia = () => !!navigator.mediaDevices?.getUserMedia; 

	
	function startCapture() {
		// webcam not associated with video element
		navigator.mediaDevices
			.getUserMedia({ video: true })
			.then((mediaStream: MediaStream) => {
				if (videoElem) {
					videoElem.srcObject = mediaStream;
					videoElem.play();
				}
			})
			.catch((err) => {
				console.error('Webcam failed to turn on', err);
			});
	}
</script>

<video bind:this={videoElem} playsinline>
	<!-- input video displayed, no captions -->
	<track kind="captions" src="" default />
</video>

<style>
	video {
		width: 640px;
		max-width: 100%;
		transform: scaleX(-1); 
	}
</style>