<script>
import  './app.css';
import 'bulma/css/bulma.css';
// Not include font file
import '@fortawesome/fontawesome-free/css/all.css'

import Title from './Title.svelte';
import Tana from './Tana.svelte';

</script>

<main>
<Title />
<Tana />
</main>

<style lang="scss">
main {
    background-color: #e6ebe0;
    text-align: center;
    padding: 2.5em;
    margin: 0 auto;
}
</style>