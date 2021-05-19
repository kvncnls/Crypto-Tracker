<script>
    export let coinProp;
</script>

<div class="coin-card">
    <img src="{coinProp.icon}" alt="" class="coin-image">
    <p class="coin-name">{coinProp.name}</p>
    <div class="coin-details">
        <div class="detail-field price-change">
            {coinProp.priceChange1w}%
        </div>
        <div class="detail-field">{coinProp.price.toFixed(2)}%</div>
        <a href={coinProp.websiteUrl} class="detail-field">Website &#8594;</a>
    </div>
</div>

<style lang="scss"> // Styling is scoped to each component

</style>