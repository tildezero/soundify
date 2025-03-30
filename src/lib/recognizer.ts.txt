
import {
	GestureRecognizer,
	FilesetResolver,
	type GestureRecognizerResult
} from '@mediapipe/tasks-vision';

/**
 * video 要素からの入力映像の解析を開始します。
 * フレームごとの認識結果はコールバック関数 `onFrame` に渡されます。
 */
export async function startRecognition(
	videoElem: HTMLVideoElement,
	onFrame: (result: GestureRecognizerResult) => void
): Promise<void> {
	const recognizer: GestureRecognizer = await createGestureRecognizer();

	// 入力映像のフレームごとの認識処理
	const renderLoop = () => {
		const result = recognizer.recognizeForVideo(videoElem, Date.now());
		onFrame(result);
		requestAnimationFrame(renderLoop);
	};

	// video 要素からのデータが取得できたらフレーム処理開始
	videoElem.addEventListener('loadeddata', renderLoop);
}

/**
 * MediaPipe のジェスチャー認識器を作成します。
 */
async function createGestureRecognizer(): Promise<GestureRecognizer> {
	const vision = await FilesetResolver.forVisionTasks(
		'https://cdn.jsdelivr.net/npm/@mediapipe/tasks-vision@latest/wasm'
	);
	return await GestureRecognizer.createFromOptions(vision, {
		baseOptions: {
			modelAssetPath:
				'https://storage.googleapis.com/mediapipe-models/gesture_recognizer/gesture_recognizer/float16/1/gesture_recognizer.task',
			delegate: 'GPU'
		},
		numHands: 2,
		runningMode: 'VIDEO'
	});
}
