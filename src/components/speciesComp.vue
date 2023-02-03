<script>

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


<template>
    <div class="card">
        <h4 class="title">{{name}}</h4>
        <div class="info">
            <h4>Classification: {{classification}}</h4>
            <h4>Designation: {{designation}}</h4>
            <h4>Average height: {{average_height}}</h4>
            <h4>Skin colors: {{skin_colors}}</h4>
            <h4>Hair colors: {{hair_colors}}</h4>
            <h4>Eye colors: {{eye_colors}}</h4>
            <h4>Average lifespan: {{average_lifespan}}</h4>
            <h4>Homeworld: {{homeworld}}</h4>
            <h4>Language: {{language}}</h4>
            <h4>People: {{people}}</h4>
            <h4>Films: {{films}}</h4>
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


