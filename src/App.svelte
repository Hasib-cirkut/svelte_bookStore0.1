<script>

import AddBookForm from './components/AddBook.svelte'

let books = [
	{
		bookName: "For whom the Bell Tolls",
		authorName: "Ernest Hemingway",
		price: 200
	},
	{
		bookName: "Kurukku",
		authorName: "Faustina Bama",
		price: 150
	},
	{
		bookName: "Shah Nama",
		authorName: "Firdausi",
		price: 250
	},
	{
		bookName: "The Castle",
		authorName: "Franz Kalka",
		price: 400
	},
]

const addNewBook = event =>{
	console.log(event.detail);

	books = [event.detail, ...books]
}

const removeBook = (bookName) =>{
	books = books.filter(book => (
		book.bookName != bookName
	))
}
	
</script>


<style>
	.card{
		display: flex;
		flex-direction: column;
		background-color: #eeee;
		margin: 10px 10px 10px 10px;
		margin-top: 7vh;
		padding-left: 20px;
		padding-right: 20px;
		font-family: Roboto;
		margin-left: 35vw;
		margin-right: 35vw;
		text-align: center;
		border-radius: 3px;
		box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.15);
		
	}

	#bookName{
		margin-top: 10px;
		margin-bottom: 10px;
	}

	#authorName{
		margin-bottom: 10px;
	}

	#bookPrice{
		margin-bottom: 15px;
	}

	.btn{
		background: rgb(116, 238, 222);
		border: 1px solid #BE9C9C;
		box-shadow: 1px 3px 4px rgba(0, 0, 0, 0.25);
		border-radius: 3px;
		
		margin: 0 auto;
		display: block;
		cursor: pointer;
		padding: 3px;
		margin-bottom: 10px;
	}

	.btn:hover{
		background: rgb(97, 206, 191);
	}

	.btn-danger{
		background: rgb(243, 96, 109);
		border: 1px solid #BE9C9C;
		box-shadow: 1px 3px 4px rgba(0, 0, 0, 0.25);
		border-radius: 0px;
		margin: 0 auto;
		display: block;
		cursor: pointer;
		padding: 2px;
		margin-bottom: 10px;
	}

	.btn-danger:hover{
		background: rgb(247, 28, 47);
	}
</style>

<AddBookForm on:addNewBook={addNewBook}/>

{#if books.length === 0}
	<p>No books available</p>
{:else}
	{#each books as book}
		<div class="card">
			<h3 id="bookName">{book.bookName}</h3>
			<p id="authorName">Author: {book.authorName}</p>
			<h4 id="bookPrice">Price: {book.price}$</h4>

			<button class="btn">Add to Cart</button>
			<button class="btn-danger" on:click={removeBook(book.bookName)}>X</button>
		</div>
	{/each}
{/if}