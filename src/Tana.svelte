<script>
let tanaData = null;

fetch('public/contents.json')
    .then((res) =>{
        return res.json();
    }).then((json) => {
        tanaData = json;
    });
</script>

{#if tanaData}
<div class="tile is-ancestor tile-root">
    {#each Object.keys(tanaData) as category}
        <div class="tile tile-divider secondary-bg">
            {category}
        </div>
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
    width: 75%;
    flex-wrap: wrap;
}
.tile-content {
    position: relative;
    flex-basis: 25%;
    max-width: 25%;
    margin-top: 1.5em;
    align-items: flex-start;    
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
    font-weight: bold;
    margin-bottom: 0;
    background: linear-gradient(transparent 80%,  $secondary 20%);
}
</style>