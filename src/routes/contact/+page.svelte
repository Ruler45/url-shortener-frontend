<script>
	let messageVisible = false;
	let message = '';
    let messageSent=false;

	const handleSubmit = async (event) => {
		event.preventDefault();
		const form = event.target;
		const data = new FormData(form);
		const body = Object.fromEntries(data);
        // console.log(messageSent);


		try {
			const response = await fetch('https://contactform-fq4a.onrender.com/api/contact', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify(body)
			});
			const result = await response.json();
			// console.log(response.status);
			message = result.message;
			form.reset();
            if(response.status<400) messageSent=true;
			
           
            // messageBox.style.backgroundColor = 'rgb(0, 255, 0)';
		} catch (error) {
			// console.log(error);
			
			message = error.message;
            messageSent=false;
		}
        // console.log(messageSent);
        messageVisible = true;

		setTimeout(() => {
			messageVisible = false;
            messageSent=false;
		}, 3000);
	};
</script>

<div class="contact-box">
	<h1 class="heading">Contact us</h1>

	<form class="form" on:submit|preventDefault={handleSubmit}>
		<input autocomplete="off" type="text" id="name" name="name" placeholder="Your name" />

		<!-- <label for="email">Email</label> -->
		<input autocomplete="off" type="email" id="email" name="email" placeholder="Your email" />

		<!-- <label for="message">Message</label> -->
		<input autocomplete="off" type="text" name="message" placeholder="Your message" />
		<button type="submit">Send</button>
	</form>
</div>

{#if messageVisible}
	<div class={`message-box ${messageSent? "sent": "fail" }`}>
		<p>{message}</p>
	</div>
{/if}

<style>
	.contact-box {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 4rem auto;
		width: 50%;
		background-color: rgb(125, 222, 246);
		backdrop-filter: blur(10px);
		border-radius: 10px;
		padding-bottom: 2rem;
	}
	.form {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
		gap: 20px;
	}
	input {
		width: 80%;
		height: 2rem;
		border-radius: 20px;
		padding: 5px 10px;
		position: relative;
		border: none;
		box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
		text-align: center;
	}

	input::before {
		position: absolute;
		left: 0;
		transform: translateX(50%);
		display: flex;
		width: 40px;
		height: 40px;
		background-color: antiquewhite;
	}
	button {
		width: 50%;
		height: 3rem;
		border-radius: 2rem;
		background-color: rgba(5, 143, 148, 0.7);
		border: none;
		cursor: pointer;
		color: white;
		font-size: 1.2rem;
		transition: 0.3s ease-in-out;
	}

	button:hover {
		/* background-color: rgb(87, 201, 247); */
		border-radius: 2rem;
		box-shadow: 0 0 10px rgb(4, 83, 114);
	}
	button:active {
		transform: scale(0.8);
	}

    .fail{
        background-color: rgb(247, 34, 23);
    }
    .sent{
        background-color: rgb(0, 255, 0);
    }
    .message-box {
        width: 50%;
        margin: 2rem auto;
        text-align: center;
        color: white;
        border-radius: 2rem;
    }

	@media screen and (max-width: 768px) {
		.contact-box {
			width: 80%;
		}
	}
</style>
