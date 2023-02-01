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
        <h4>{{name}}</h4>
        <h4>model: {{model}}</h4>
        <h4>manufacturer: {{manufacturer}}</h4>
        <h4>cost_in_credits: {{cost_in_credits}}</h4>
        <h4>length: {{length}}</h4>
        <h4>max_atmosphering_speed: {{max_atmosphering_speed}}</h4>
        <h4>crew: {{crew}}</h4>
        <h4>passengers: {{passengers}}</h4>
        <h4>cargo_capacity: {{cargo_capacity}}</h4>
        <h4>consumables: {{consumables}}</h4>
        <h4>hyperdrive_rating: {{crew}}</h4>
        <h4>MGLT: {{MGLT}}</h4>
        <h4>starship_class: {{starship_class}}</h4>
        <h4>pilots: {{pilots}}</h4>
    </div>

</template>