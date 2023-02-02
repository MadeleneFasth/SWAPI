<script>
// import { registerRuntimeCompiler } from 'vue';

export default {
    props: ['name', 
    'model',
    'manufacturer',
    'cost_in_credits',
    'length',
    'max_atmosphering_speed',
    'crew',
    'passengers',
    'cargo_capacity',
    'consumables',
    'hyperdrive_rating',
    'MGLT',
    'starship_class',
    'pilots'
]    
}

</script>


//nästa steg att ta ut info från api vägen (films, species etc.)
<template>
    <div class="card">
        <h4 class="title">{{name}}</h4>
        <div class="info">
            <h4>Model: {{model}}</h4>
            <h4>Manufacturer: {{manufacturer}}</h4>
            <h4>Cost in credits: {{cost_in_credits}}</h4>
            <h4>Length: {{length}}</h4>
            <h4>Max atmosphering speed: {{max_atmosphering_speed}}</h4>
            <h4>Crew: {{crew}}</h4>
            <h4>Passengers: {{passengers}}</h4>
            <h4>Cargo capacity: {{cargo_capacity}}</h4>
            <h4>Consumables: {{consumables}}</h4>
            <h4>Hyperdrive rating: {{crew}}</h4>
            <h4>MGLT: {{MGLT}}</h4>
            <h4>Starship_class: {{starship_class}}</h4>
            <h4>Pilots: {{pilots}}</h4>
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

</style>

