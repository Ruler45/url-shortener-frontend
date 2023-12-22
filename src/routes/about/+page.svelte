<script>
import TechStack from "../../component/tech-stack/Tech_stack.svelte";
import data from "./data.json";
console.log(data);

</script>





<h1 class="title">About Us</h1>
<main>
	<p>
		Tired of lengthy, unwieldy URLs cramping your tweets and messages? Introducing PocketLinks, your
		friendly neighborhood URL shortener! We transform those cumbersome monsters into bite-sized
		links, saving you precious space and sanity.
	</p>

	<div class="working">
		<h3>How does it work?</h3>
		<ul>
			<li>Paste your long URL: Simply drop your URL into the PocketLinks input field.</li>
			<li>Click & shrink: Hit the "Shorten" button, and watch your link magically shrink!</li>
			<li>
				Share & shine: Copy the newly minted short URL and share it freely across your platforms.
			</li>
		</ul>
	</div>

	<div class="tech-stacks">
		<h3>What technologies are used?</h3>
		{#each data as tech}
		<TechStack
			imageUrl={tech.imageUrl}
			desc={tech.desc}
			title={tech.title}/>
		{/each}
	</div>
</main>

<style>
	.title {
		text-align: center;
		font-size: 2.5rem;
		margin: 2rem;
		color: rgb(237, 120, 17);
		font-family: Montserrat, sans-serif;
	}
    main{
        display: flex;
        flex-direction: column;
        align-items: center;
        font-size: 1.2rem;
        gap: 20px;
        width: 80%;
        margin-inline: auto;
        margin-top: 2rem;
    }
	.tech-stacks {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 20px;
		width: 100%;
	}
</style>
