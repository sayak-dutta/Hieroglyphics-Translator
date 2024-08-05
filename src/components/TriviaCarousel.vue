<template>
	<div class="trivia-carousel">
		<div class="trivia-text" :class="{ 'fade-in': isFadingIn, 'fade-out': isFadingOut }">
			{{ currentTrivia }}
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			triviaList: [
				"The Great Pyramid of Giza is one of the Seven Wonders of the Ancient World.",
				"Ancient Egyptian writing, known as hieroglyphics, was used for over 3,000 years.",
				"The Rosetta Stone was crucial in deciphering Egyptian hieroglyphics.",
				"The discovery of Tutankhamun's tomb led to the myth of the 'Curse of the Pharaohs.'",
				"Ancient Egyptians practiced mummification to preserve bodies for the afterlife.",
				"Cleopatra VII was the last Pharaoh of Egypt, known for her intelligence and political acumen.",
				"The Great Sphinx of Giza is associated with various myths and legends.",
				"Ancient Egyptians were among the first to use sundials to measure time.",
				"Pharaohs were buried with elaborate golden masks to ensure safe passage to the afterlife.",
				"Ancient Egyptians worshipped a vast pantheon of gods, including Ra and Osiris.",
				"Cleopatra VII is said to have had a vast library in Alexandria.",
				"Egyptians practiced advanced medicine for their time, using herbs and surgery.",
				"The Great Sphinx of Giza is missing its nose, possibly due to erosion or vandalism.",
				"Scarabs were considered sacred, symbolizing protection and rebirth.",
				"According to Greek historians, there was a massive labyrinth in Egypt, whose exact location is unknown.",
			],
			currentIndex: 0,
			isFadingIn: true,
			isFadingOut: false,
		};
	},
	computed: {
		currentTrivia() {
			return this.triviaList[this.currentIndex];
		},
	},
	methods: {
		switchTrivia() {
			this.isFadingOut = true;
			setTimeout(() => {
				this.currentIndex = (this.currentIndex + 1) % this.triviaList.length;
				this.isFadingOut = false;
				this.isFadingIn = true;
				setTimeout(() => {
					this.isFadingIn = false;
				}, 1000);
			}, 1000);
		},
	},
	mounted() {
		setInterval(this.switchTrivia, 10000); // Switch trivia every 10 seconds
	},
};
</script>

<style scoped>
.trivia-carousel {
	position: fixed;
	bottom: 0;
	left: 0;
	width: 100%;
	background: rgba(0, 0, 0, 0.7);
	color: white;
	text-align: center;
	padding: 10px;
	font-size: 20px;
}

.trivia-text {
	transition: opacity 1s ease-in-out;
	opacity: 1;
}

.fade-out {
	opacity: 0;
}

.fade-in {
	opacity: 1;
}
</style>
