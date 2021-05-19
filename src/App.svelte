<script>
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