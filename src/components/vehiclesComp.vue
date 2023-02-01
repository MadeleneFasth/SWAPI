<script>

export default {
    props: [
    'name', 
    "model",
    "manufacturer",
    "cost_in_credits",
    "length",
    "max_atmosphering_speed",
    "crew",
    "passengers",
    "cargo_capacity",
    "consumables",
    "vehicle_class",
    "pilots",
    "films"
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
        <h4>vehicle_class: {{vehicle_class}}</h4>
        <h4>vehicle_class: {{pilots}}</h4>
        <h4>films: <a href={{films}}>Go to films</a></h4>
    </div>

</template>