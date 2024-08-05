<template>
	<TriviaCarousel />
	<h1 class="heading">Hieroglyphics Translator</h1>
	<ConverterInput />
	<MusicPlayer />
	<HieroglyphicsTranslator />
</template>

<script>
import HieroglyphicsTranslator from "./components/HieroglyphicsTranslator.vue";
import MusicPlayer from "./components/MusicPlayer.vue";
import TriviaCarousel from "./components/TriviaCarousel.vue";
import "primeicons/primeicons.css";

export default {
	name: "App",
	components: {
		HieroglyphicsTranslator,
		MusicPlayer,
		TriviaCarousel,
	},
};
</script>

<style>
* {
	margin: 0px;
}
.heading {
	color: white;
	font-size: 50px;
	margin-bottom: 100px;
}
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin: 0px;
	background: radial-gradient(rgba(0, 0, 0, 0.436), rgb(71, 57, 20)), url(./assets/bg.webp);
	background-repeat: no-repeat;
	background-size: auto;
	background-repeat: repeat-x;
	animation: slideBackground 40s linear infinite;
	height: 100vh;
}
@keyframes slideBackground {
	from {
		background-position: 0 0;
	}
	to {
		background-position: -1600px 0;
	}
}
</style>
