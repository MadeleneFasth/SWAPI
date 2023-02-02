<script>
// import { registerRuntimeCompiler } from 'vue';

export default {
    props: ['name', 
    'height',
    'hair_color',
    'skin_color',
    'eye_color',
    'birth_year',
    'gender',
    'homeworld',
    'films',
    'species',
    'vehicles',
    'starships',
    'homeworld'
]    
}

</script>


//nästa steg att ta ut info från api vägen (films, species etc.)
<template>
    <div class="card">
        <h4 class="title">{{name}}</h4>
        <h4>Height: {{height}}</h4>
        <h4>hair color: {{hair_color}}</h4>
        <h4>skin_color: {{skin_color}}</h4>
        <h4>eye_color: {{eye_color}}</h4>
        <h4>birth_year: {{birth_year}}</h4>
        <h4>gender: {{gender}}</h4>
        <h4>homeworld: <a href={{homeworld}}>Go to homeworld</a></h4>
        <h4>films: <a href={{films}}>Go to films</a></h4>
        <h4>species: <a href={{species}}>Go to species</a></h4>
        <h4>vehicles: <a href={{vehicles}}>Go to vehicles</a></h4>
        <h4>starships: <a href={{starships}}>Go to starships</a></h4>
    </div>
</template>

<style>
.title {

}
</style>