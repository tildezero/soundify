<script lang="ts">
	/** Webcam による映像キャプチャを開始するためのフラグ */
	export let active: boolean = false;

	/** video 要素の bind 用 */
	export let videoElem: HTMLVideoElement | undefined;

	$: if (active) {
		startCapture();
	}

	function startCapture() {
		// Web カメラのストリームを取得して video 要素に紐付ける
		navigator.mediaDevices
			.getUserMedia({ video: true })
			.then((mediaStream: MediaStream) => {
				if (videoElem) {
					videoElem.srcObject = mediaStream;
					videoElem.play();
				}
			})
			.catch((err) => {
				console.error('Web カメラの取得に失敗しました:', err);
			});
	}
</script>

<video bind:this={videoElem} playsinline>
	<!-- Web カメラの入力映像を表示するのでキャプションは存在しない -->
	<track kind="captions" src="" default />
</video>

<style>
	video {
		width: 640px;
		max-width: 100%;
		transform: scaleX(-1); /* 映像を左右反転 */
	}
</style>