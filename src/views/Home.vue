<template>
	<div class="home">
		<h1>Game of thrones books</h1>
		<!-- <img alt="Vue logo" src="../assets/logo.png">
		<HelloWorld msg="Welcome to Your Vue.js App"/> -->
		<v-card v-for="book in this.books" :key="book.isbn" :id="book.isbn" :details="book.name" class="listItem">
			<v-card-text class="gridEl">
				<span class="gridItem">Name:</span>
				<span class="gridItem">{{ book.name }}</span>
			</v-card-text>
			<v-card-title class="gridEl">
				<span class="gridItem">First author: </span>
				<span class="gridItem">{{ book.authors[0] }}</span>
			</v-card-title>
			<v-card-text class="gridEl">
				<span class="gridItem">Date released: </span>
				<span class="gridItem">{{ new Date(book.released).toDateString() }}</span>
			</v-card-text>
			<v-card-actions>
				<router-link :to="{ name: 'BookDetails', params: {bookId: Number(book.url.split('/').slice(-1)[0])} }" class="btn">
					<button>More details</button>
				</router-link>
			</v-card-actions>
		</v-card>
	</div>
</template>

<script>
// @ is an alias to /src
import books from '@/books.json';

export default {
	name: 'Home',
	/*components: {
		HelloWorld
	}*/
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
