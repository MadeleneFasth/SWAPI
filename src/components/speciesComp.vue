<script>
// import { registerRuntimeCompiler } from 'vue';

export default {
    props: ['name', 
    'classification',
    'designation',
    'average_height',
    'skin_colors',
    'hair_colors',
    'eye_colors',
    'average_lifespan',
    'homeworld',
    'language',
    'people',
    'films',
]    
}

</script>


//nästa steg att ta ut info från api vägen (films, species etc.)
<template>
    <div class="card">
        <h4>{{name}}</h4>
        <h4>classification: {{classification}}</h4>
        <h4>designation: {{designation}}</h4>
        <h4>average_height: {{average_height}}</h4>
        <h4>skin_colors: {{skin_colors}}</h4>
        <h4>hair_colors: {{hair_colors}}</h4>
        <h4>eye_colors: {{eye_colors}}</h4>
        <h4>average_lifespan: {{average_lifespan}}</h4>
        <h4>homeworld: {{homeworld}}</h4>
        <h4>language: {{language}}</h4>
        <h4>people: {{people}}</h4>
        <h4>films: {{films}}</h4>
    </div>

</template>

