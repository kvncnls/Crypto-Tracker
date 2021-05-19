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
	<button on:click="{fetchCoins}">Fetch Coin Data!</button>

	{#each coins as coin}
		<CoinCard coinProp={coin}/>
	{/each}

</main>

<style lang="scss">

</style>