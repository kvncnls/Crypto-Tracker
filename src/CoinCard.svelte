<script>
    export let coinProp;
</script>

<div class="coin-card">
    <img src="{coinProp.icon}" alt="" class="coin-image">
    <p class="coin-name">{coinProp.name}</p>
    <div class="coin-details">
        <div class="detail-field price-change">
            <h4>1 Week Price Change: </h4><p>{coinProp.priceChange1w}%</p>
        </div>
        <div class="detail-field">
            <h4>Current Price: </h4><p>{coinProp.price.toFixed(2)}$</p>
        </div>
        <a href={coinProp.websiteUrl} class="detail-field">Website &#8594;</a>
    </div>
</div>

<style lang="scss"> // Styling is scoped to each component

    .coin-card {
        background-color: white;
        border-radius: 20px;
        --tw-shadow: 0 20px 25px -5px rgba(0,0,0,0.1), 0 10px 10px -5px rgba(0,0,0,0.04);
        box-shadow:
        var(--tw-ring-offset-shadow, 0 0 #0000),
        var(--tw-ring-shadow, 0 0 #0000),
        var(--tw-shadow);

        .coin-image {
            max-width: 4em;
            margin-top: 10px;
        }

        .coin-name {
            font-size: 1.5rem;
            font-weight: bold;
            margin-top: 15px;
        }

        .coin-details {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            border-top: 1px solid #d1d5db;
            background-color: #f3f4f6;

            .detail-field {
                display: flex;
                align-items: center;
                font-size: 1rem;
                font-weight: normal;
                padding: 15px 0;

                @media (min-width: 1024px) {
                    font-size: 1.1rem;
                    padding: 15px;
                }

                h4 {
                    margin: 0 1em;
                }

                &:not(:last-child) {
                    border-right: 1px solid #d1d5db;
                }
            }

            .price-change {
                color: #dc2626;
            }

            .positive {
                color: #16a34a;
            }

        }
    }

</style>