<script>

import { Collapse } from 'svelma'

let tanaData = null;

fetch('public/contents.json')
    .then((res) =>{
        return res.json();
    }).then((json) => {
        tanaData = json;
    });
</script>

{#if tanaData}
<div class="tile tile-root">
    {#each Object.keys(tanaData) as category}
    <Collapse open={false}>
        <div class="tile tile-divider secondary-bg" slot="trigger">
            {category}
        </div>

        <div class="tile-content-area">
            {#each tanaData[category] as item}
            <div class="tile is-parent tile-content">
                <div class="card">
                    <div class="card-image">
                        <figure class="image">
                            {#if item.image}
                                <img src="{item.image}" alt="">
                            {:else}
                                <img src="https://s0.wp.com/mshots/v1/{item.url}" alt="">
                            {/if}
                        </figure>
                    </div>
                    <div class="card-content">
                        <p class="title">{item.title}</p>
                        <p class="subtitle">{item.description}</p>
                    </div>
                </div>
                <a href="{item.url}" class="tile-link"> </a>
            </div>
            {/each}
        </div>

    </Collapse>
    {/each}
</div>
{/if}

<style lang="scss">
@import './Theme.scss';
.title, .subtitle {
    text-align: left;
}
.title {
    font-size: 1.5em;
}
.subtitle {
    font-size: 0.7em;
}
.tile-root{
    margin: 0 auto !important;
    width: 100%;
    flex-wrap: wrap;
}
.tile-content-area {
    display: flex;
    flex-wrap: wrap;
}
.tile-content {
    position: relative;
    flex-basis: 25%;
    max-width: 25%;
    margin-top: 1.5em;
    align-items: flex-start;
}
.card {
    border-radius: 15px;
}
.tile-link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height:100%;
}
.tile-divider {
    flex-basis: 100%;
    font-size: 1.5em;
    font-weight: 1.5;
    margin-bottom: 0;
    cursor: pointer;
    background: linear-gradient(transparent 97%,  $secondary 3%);
    width: 100%;
}
.card-image img {
    border-radius: 15px 15px 0 0;
}
</style>