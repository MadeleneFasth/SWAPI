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
            <div class="info">
                <h4>Height: {{height}}</h4>
                <h4>Hair color: {{hair_color}}</h4>
                <h4>Skin color: {{skin_color}}</h4>
                <h4>Eye color: {{eye_color}}</h4>
                <h4>Birth year: {{birth_year}}</h4>
                <h4>Gender: {{gender}}</h4>
                <h4>Homeworld: <a href={{homeworld}}>Go to homeworld</a></h4>
                <h4>Films: <a href={{films}}>Go to films</a></h4>
                <h4>Species: <a href={{species}}>Go to species</a></h4>
                <h4>Vehicles: <a href={{vehicles}}>Go to vehicles</a></h4>
                <h4>Starships: <a href={{starships}}>Go to starships</a></h4>
            </div>
    </div>
</template>

<style scoped>
    .title {
        font-size: 30px;
        margin-bottom: 1rem;
    }

    .info h4 {
        margin-bottom: 0.5rem;
    }

    a {
        
    }
</style>



