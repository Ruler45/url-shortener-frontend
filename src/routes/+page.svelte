
<script>
import axios from 'axios';


const handleSubmit= async ()=>{
    const urlInput = document.querySelector('.url-input');
    const shortURL = document.querySelector('.shortURL-box');
    const originalUrl = urlInput.value;

    axios.post('https://url-shortener-61u7.onrender.com/api/url', {
		originalUrl
	}).then((response) => {
		// console.log(response.data);
		shortURL.value =`url-shortener-61u7.onrender.com${response.data.shortUrl}` ;
	}).catch((error) => {
		console.log(error.response);
		if(error.response.status===403){
			shortURL.value =`url-shortener-61u7.onrender.com${error.response.data.shortUrl}` ;
		}

	});
}

</script>






<h1 class="title">Welcome to URL Shortening Service</h1>

<form  class="form" method="POST" on:submit|preventDefault={handleSubmit}>
	<div class="input-box">
		<input class="url-input" type="text" placeholder="Enter your URL here" />
		<button class="shorten-button">Shorten</button>
	</div>
    <input  class="shortURL-box" placeholder="Shortened URL" readonly type="text">
</form>

<style>
	.title {
		text-align: center;
		font-size: 2.5rem;
		margin: 3rem;
		color: rgb(237, 120, 17);
		font-family: Montserrat, sans-serif;
	}

    .form{
        display: flex;
        flex-direction: column;
        /* align-items: center; */
        gap:20px;
        width: 70%;
        margin-inline: auto;
        margin-top: 5rem;
    }
	.input-box {
		display: flex;
		align-items: center;
		flex-direction: row;
		gap: 10px;
        /* width: 100%; */
        widows: 80%;
	}
    
	.url-input {
		width: 30rem;
		height: 2rem;
		border-radius: 5px;
		border: 1px solid rgb(237, 120, 17);
		padding: 0.5rem;
		font-size: 1rem;
		font-family: Montserrat, sans-serif;
	}
    .shortURL-box{
        display: flex;
        width: 25rem;
        height: 2rem;
		border-radius: 5px;
        justify-self: flex-start;
		border: 1px solid rgb(237, 120, 17);
		padding: 0.5rem;
		font-size: 1rem;
		font-family: Montserrat, sans-serif;
    }
	.shorten-button {
		display: flex;
		height: 100%;
		border-radius: 5px;
		border: 1px solid rgb(237, 120, 17);
		padding: 0.5rem;
		font-size: 1rem;
		font-family: Montserrat, sans-serif;
		background-color: rgb(237, 120, 17);
		color: white;
		cursor: pointer;
		transition: 0.3s ease-in-out;

		&:hover {
			background-color: rgb(237, 120, 17, 0.8);
			transform: scale(1.2);
		}
		&:active {
			transform: scale(1);
		}
	}
</style>
