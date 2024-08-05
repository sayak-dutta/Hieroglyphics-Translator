<template>
	<div class="music-player">
		<audio ref="audio" :src="currentTrack"></audio>
		<button class="music-button" @click="togglePlay">
			<i v-if="isPlaying" class="pi pi-pause-circle"></i>
			<i v-else class="pi pi-play-circle"></i>
		</button>
	</div>
</template>

<script>
import egyptianMusic from "@/assets/bgm.mp3";
import anotherEgyptianMusic from "@/assets/ancient.mp3";

export default {
	data() {
		return {
			isPlaying: false,
			currentTrack: egyptianMusic,
			tracks: [egyptianMusic, anotherEgyptianMusic],
			currentTrackIndex: 0,
		};
	},
	methods: {
		togglePlay() {
			const audio = this.$refs.audio;
			if (this.isPlaying) {
				audio.pause();
			} else {
				audio.play().catch(() => {
					alert('Click "Play" to start the music.');
				});
			}
			this.isPlaying = !this.isPlaying;
		},
		nextTrack() {
			this.currentTrackIndex = (this.currentTrackIndex + 1) % this.tracks.length;
			this.currentTrack = this.tracks[this.currentTrackIndex];
			if (this.isPlaying) {
				this.$refs.audio.play().catch(() => {
					alert('Click "Play" to start the music.');
				});
			}
		},
	},
};
</script>

<style scoped>
.music-player {
	position: fixed;
	bottom: 60px;
	right: 10px;
}

.music-button {
	background-color: #b59815;
	border: none;
	border-radius: 50%;
	color: white;
	padding: 10px;
	cursor: pointer;
}

.music-button:hover {
	background-color: #5d4915;
}

.pi {
	font-size: 24px;
}
</style>
