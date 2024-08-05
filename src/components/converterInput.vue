<template>
	<div>
		<h2>String Manipulation</h2>
		<input v-model="inputText" placeholder="Enter text" />
		<button @click="reverseString">Reverse String</button>
		<p>Reversed: {{ reversedText }}</p>
	</div>
</template>

<script>
export default {
	data() {
		return {
			inputText: "",
			reversedText: "",
		};
	},
	methods: {
		reverseString() {
			this.reversedText = this.inputText.split("").reverse().join("");
		},
	},
};
</script>

<style scoped>
input {
	margin-right: 10px;
}
</style>
