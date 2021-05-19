<script>
    export let coinProp;

    function changeIsPositive(priceChange){
      return priceChange >= 0;
    }
</script>

<div class="coin-card">
    <img src="{coinProp.icon}" alt="" class="coin-image">
    <p class="coin-name">{coinProp.name}</p>
    <div class="coin-details">
        <div class="detail-field price-change" class:positive={changeIsPositive(coinProp.priceChange1w)}>
            {coinProp.priceChange1w}%
        </div>
        <div class="detail-field">
            ${coinProp.price.toFixed(2)}
        </div>
        <a href={coinProp.websiteUrl} class="detail-field">Website &#8594;</a>
    </div>
</div>

<style lang="scss"> // Styling is scoped to each component

.coin-card {
    background-color: white;
    border-radius: 20px;
    --tw-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),
      var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}
.coin-image {
  max-width: 4rem;
  margin-top: 10px;
}
.coin-name {
  font-size: 24px;
  font-weight: bold;
  margin-top: 15px;
}
.coin-details {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  border-top: 1px solid #d1d5db;
  background-color: #f3f4f6;
}

.detail-field {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  padding: 15px 0;
  font-weight: normal;

  &:not(:last-child) {
    border-right: 1px solid #d1d5db;
  }

}

.price-change {
  color: #dc2626;
}

.positive {
  color: green;
}

</style>