<script>

    import {createEventDispatcher} from 'svelte'

    const dispatcher = createEventDispatcher()

    let bookName = ''
    let authorName = ''
    let price = 0

    const onSubmit = e =>{
        e.preventDefault()
        
        dispatcher('addNewBook', {bookName, authorName, price})
    }

</script>

<style>

    .addBook{
        display: flex;
        flex-direction: column;
        height: 20vh;
        margin-left: 30vw;
        margin-right: 30vw;
        text-align: center;
    }

    #bookName, #authorName, #price, button{
        padding: 2px;
        margin: 0 auto;
		display: block;
		background: rgb(226, 226, 226);
        border: 1px solid rgb(236, 235, 235);
        box-shadow: 0px 4px 2px rgba(0, 0, 0, 0.19);
    }

    #bookName{
        margin-top: 2vh;
    }

    button{
        margin-bottom: 2vh;
    }

</style>


<div class="addBook">
    <form on:submit={onSubmit}>
        <input type="text" id="bookName" placeholder="Enter Book Name" bind:value={bookName}><br />
        <input type="text" id="authorName" placeholder="Enter Author Name" bind:value={authorName}> <br/>
        <input type="number" id="price" placeholder="Enter price" bind:value={price}><br />
        <button>Add Book</button>
    </form>
</div>