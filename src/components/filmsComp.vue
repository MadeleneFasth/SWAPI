<script>
// import { registerRuntimeCompiler } from 'vue';

export default {
    props: [
    "title",
    "episode_id", 
    "opening_crawl",   
    'director',
    "producer",
    "release_date",
    'characters', 
    "planets", 
    "starships",
    "vehicles", 
    "species" 
 ] 
}

</script>

//nästa steg att ta ut info från api vägen (films, species etc.)
<template>
    <div class="card">
        <h4>{{title}}</h4>
        <h4>Episode: {{episode_id}}</h4>
        <h4>Opening_crawl: {{opening_crawl}}</h4>
        <h4>Director: {{director}}</h4>
        <h4>Producer: {{producer}}</h4>
        <h4>Release date: {{release_date}}</h4>
        <h4>Characters <a href={{characters}}>Go to characters</a></h4>
        <h4>Planets: <a href={{planets}}>Go to planets</a></h4>
        <h4>Starships: <a href={{starships}}>Go to starships</a></h4>
        <h4>Vehicles: <a href={{vehicles}}>Go to vehicles</a></h4>
        <h4>Species: <a href={{species}}>Go to species</a></h4>
    </div>

</template>
