<script>

	/* FEATURES TO ADD: */
	// 1. Add an input field where the user can write a coin name to filter the results
	// 2. Allow the user to fetch more coins with a “Load More” button
	// 3. Make each coin clickable to show more data on that coin
	// 4. Show a graph of price changes for a specific coin
	// 5. Allow the user to sort the coins by percentage growth or current price
	// 6. Deploy the project to Netlify

	import CoinCard from "./CoinCard.svelte";

	let name = "Crypto Tracker";

	let coins = [];

	async function fetchCoins(){
		const response = await fetch("https://api.coinstats.app/public/v1/coins?skip=0&limit=50");
		const data = await response.json();
		coins = data.coins;

		console.log("coins:", coins);
	}
</script>

<main>
	<h1>{name}</h1>
	{#if coins.length === 0}
		<button on:click="{fetchCoins}">Fetch Coin Data!</button>
	{:else}
		<div class="grid">
			{#each coins as coin}
				<CoinCard coinProp={coin}/>
			{/each}
		</div>
	{/if}


</main>

<style lang="scss">

	main {
		text-align: center;
		padding: 40px 0;
		margin: 0 auto;
		@media screen and (min-width: 640px) {
			max-width: 1600px;
			padding: 40px 20px;
		}
	}

	h1 {
			color: #ff3e00;
			text-transform: uppercase;
			font-size: 4rem;
			font-weight: 100;
		}

	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
		gap: 30px;
	}

</style>