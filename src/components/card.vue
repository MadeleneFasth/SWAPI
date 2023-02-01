<script>
// import { registerRuntimeCompiler } from 'vue';

export default {
    props: ['name', 
    'height']    
}

</script>

<template>

       
    <div class="card">
    <h4>{{name}}</h4>
    <h4>Height: {{height}}</h4>
    <h4>hair color: {{hair_color}}</h4>
    <h4>skin_color: {{skin_color}}</h4>
    <h4>eye_color: {{eye_color}}</h4>
    <h4>birth_year: {{birth_year}}</h4>
    <h4>gender: {{birth_year}}</h4>
    <h4>homeworld: <a href={{homeworld}}>Go to homeworld</a></h4>
    </div>


</template>