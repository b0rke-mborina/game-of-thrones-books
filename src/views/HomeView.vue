<template>
  <hello-world />
</template>

<script>
import HelloWorld from '../components/HelloWorld'

export default {
	name: 'Home',

	// components: {
		// HelloWorld,
	// },
	data() {
		return {
			books,
		}
	},
	methods: {
		async mounted() {
			// let apiResponse = await fetch("@/books.json");
			// this.books = await apiResponse.json()
			console.log(this.books);
		}
	}
}
</script>
