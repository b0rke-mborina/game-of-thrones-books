<template>
	<div class="home">
		<h1>Game of thrones books</h1>
		<!-- <img alt="Vue logo" src="../assets/logo.png">
		<HelloWorld msg="Welcome to Your Vue.js App"/> -->
		<v-container column v-if="book" class="mainDiv">
		<v-card class="commitCard">
			<v-card-title class="gridDiv">
				<span class="gridItem">Book</span>
				<strong class="gridItem">[{{ bookId }}]</strong>
			</v-card-title>
			<div>
				<div class="gridDiv">
					<strong class="gridItem">Authors: </strong>
					<span v-for="author in book.authors" :key="author.value">
						{{ author }}
					</span>
				</div>
				<div class="gridDiv">
					<strong class="gridItem">ISBN:</strong>
					<span class="gridItem">{{ book.isbn }}</span> 
				</div>
				<div class="gridDiv">
					<strong class="gridItem">Number of pages:</strong>
					<span class="gridItem">{{ book.numberOfPages }}</span> 
				</div>
				<div class="gridDiv">
					<strong class="gridItem">Publisher:</strong>
					<span class="gridItem">{{ book.publisher }}</span> 
				</div>
				<div class="gridDiv">
					<strong class="gridItem">Country of origin:</strong>
					<span class="gridItem">{{ book.country }}</span> 
				</div>
				<div class="gridDiv">
					<strong class="gridItem">Number of characters:</strong>
					<span class="gridItem">{{ book.characters.length }}</span> 
				</div>
			</div>
		</v-card>
		<v-card-actions>
			<button color="error" @click="returnHome" class="backBtn">Back</button>
		</v-card-actions>
	</v-container>
	</div>
</template>

<script>
// @ is an alias to /src
import books from '@/books.json';

export default {
	name: 'BookDetails',
	data() {
		return {
			books,
			book: null,
			bookId: this.$route.params.bookId,
		}
	},
	async mounted() {
		// console.log("here");
		let apiResponse = await fetch("http://ntankovic.unipu.hr:8000/api/books/" + this.bookId);
		this.book = await apiResponse.json()
		console.log(this.book);
	},
	methods: {
		returnHome() {
			this.$router.replace({ name: "Home" });
		},
	}
}
</script>