<script>

export default {
    props: ['name', 
    'rotation_period',
    'orbital_period',
    'diameter',
    'climate',
    'gravity',
    'terrain',
   'surface_water',
   'population',
   'residents',
   'films'
]
}



</script>

<template>
    <div class="card">
        <h4 class="title">{{name}}</h4>
        <div class="info">
            <h4>rotation_period: {{rotation_period}}</h4>
            <h4>orbital_period: {{orbital_period}}</h4>
            <h4>diameter: {{diameter}}</h4>
            <h4>climate: {{climate}}</h4>
            <h4>gravity: {{gravity}}</h4>
            <h4>terrain: {{terrain}}</h4>
            <h4>surface_water: {{surface_water}}</h4>
            <h4>population: {{population}}</h4>
            <h4>residents: <a href={{residents}}>Go to residents</a></h4>
            <h4>films: <a href={{films}}>Go to films</a></h4>
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