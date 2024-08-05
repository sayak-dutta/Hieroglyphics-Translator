<template>
	<div class="translator-container">
		<div style="box-shadow: 0px 4px 20px 1px black">
			<div class="translator-content">
				<input
					type="text"
					v-model="inputText"
					@input="translateText"
					placeholder="Type here..."
					class="translator-input"
				/>
				<div class="translated-text" ref="translatedText">{{ translatedText }}</div>
				<div class="buttons">
					<button @click="copyToClipboard" title="Copy to Clipboard">
						<i class="pi pi-copy"></i>
					</button>

					<button @click="downloadImage" title="Download as Image">
						<i class="pi pi-download"></i>
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import { saveAs } from "file-saver";
import html2canvas from "html2canvas";

export default {
	data() {
		return {
			inputText: "",
			translatedText: "",
		};
	},
	methods: {
		translateText() {
			const hieroglyphicsMap = {
				A: "𓄿",
				B: "𓃀",
				C: "𓍿",
				D: "𓂧",
				E: "𓇋",
				F: "𓆑",
				G: "𓎼",
				H: "𓉔",
				I: "𓇋",
				J: "𓆓",
				K: "𓎡",
				L: "𓃭",
				M: "𓈖",
				N: "𓈖",
				O: "𓂝",
				P: "𓊪",
				Q: "𓎤",
				R: "𓂋",
				S: "𓋴",
				T: "𓏏",
				U: "𓅱",
				V: "𓆑",
				W: "𓅱",
				X: "𓐙",
				Y: "𓇋",
				Z: "𓊃",
			};
			this.translatedText = this.inputText
				.toUpperCase()
				.split("")
				.map((char) => hieroglyphicsMap[char] || char)
				.join("");
		},
		copyToClipboard() {
			navigator.clipboard.writeText(this.translatedText).then(() => {
				alert("Copied to clipboard!");
			});
		},
		downloadImage() {
			html2canvas(this.$refs.translatedText, { scale: 5 }).then((canvas) => {
				canvas.toBlob((blob) => {
					saveAs(blob, "hieroglyphs.png");
				});
			});
		},
	},
};
</script>

<style scoped>
@font-face {
	font-family: "Hieroglyphs";
	src: url("@/assets/font.otf") format("opentype");
}
.translator-container {
	position: relative;
	max-width: 600px;
	margin: 0 auto;
	padding: 20px;
}

.blurred-background {
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	background: rgba(255, 255, 255, 0.8);
	backdrop-filter: blur(10px);
	border-radius: 10px;
	z-index: -1;
}

.translator-content {
	position: relative;
	background: white;
	padding: 20px;
	box-shadow: inset #b59815 0 0 0 5px, inset #5d4915 0 0 0 1px, inset #5d4915 0 0 0 0px,
		inset #5d4915 0 0 0 9px;
}

.translator-input {
	width: 100%;
	border: none;
	border-bottom: 2px solid black;

	font-size: 28px;
	background: transparent;
	outline: none;
}

.translated-text {
	margin-top: 10px;
	font-size: 32px;
	font-family: "Hieroglyphs", sans-serif;
}
.buttons {
	padding-top: 20px;
}
.buttons button {
	margin: auto 10px;
	transition: 0.3s ease-in-out;
	border: 1px solid #5d4915;
}
button {
	background: #b59815;
	border-radius: 5px;
	border: none;
	padding: 5px;
	font-size: 18px;
}

button:hover {
	background-color: #a07b45;
	/* transition: 1s ease-in-out; */
}
</style>
