<script>
import  './app.css';
import 'bulma/css/bulma.css';
import { afterUpdate } from 'svelte';
import { library, icon } from '@fortawesome/fontawesome-svg-core'
import { faSquareGithub } from '@fortawesome/free-brands-svg-icons'
library.add(faSquareGithub)

import Title from './Title.svelte';
import Tana from './Tana.svelte';

const squareGithub = icon(faSquareGithub, {transform: {size: 32}});
let squareGithubIcon = squareGithub.html;
let mainArea;

window.addEventListener('scroll', () => {
    console.log(mainArea.scrollHeight, document.body.style.height);
	document.body.style.height = mainArea.scrollHeight + "px";
});

</script>


<main bind:this={mainArea}>
    <div class="columns">
        <div class="column is-1">
            <Title />
        </div>
        <div class="column">
            <Tana />
        </div>
    </div>
    <div class="icon-area">
        <a href="https://github.com/sabiz/Tana">
            {@html squareGithubIcon}
        </a>
    </div>
</main>

<style lang="scss">

@import './Theme.scss';

main {
    color: $text;
    text-align: center;
    padding-top: 1.5em;
    padding-bottom: 2.5em;
    margin: 0 auto;
}
.icon-area {
    position: fixed;
    top: 5px;
    right: 10px;
}
.icon-area a {
    color: $text;
}
</style>