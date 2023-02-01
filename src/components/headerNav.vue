<script>
// import { VueElement } from 'vue';
import subCategories from './subCategories.vue';

  export default {
    components: {
        subCategories
    },
        data() {
            return {
                listItems: [],
                item: {
                }, 
                characters: [],
                clickedName: ''
            }
        },
        mounted() {
            fetch("https://swapi.dev/api/?format=json")
            .then(res => res.json())
            .then(data => this.listItems = data)
            .catch(err => console.log(err.message))
        },
        methods: {
                
                async doThisOnClick() {
                    const res = await fetch("https://swapi.dev/api/people/?format=json");
                    const finalRes = await res.json();
                    this.item = finalRes;
                    this.characters = finalRes.results;
                    console.table(finalRes.results)
                }
            },
    }


</script>



<template>

    <nav>
        <li v-for="(path, title) in listItems">
        <!-- <a v-bind:href="item">{{index}}</a> -->
        <button @click="doThisOnClick">{{title}}</button>
        </li>
    </nav>

</template>


<style>

nav {
    display: flex;
    justify-content: space-around;
    align-items: flex-end;

    height: 8em;
}

li {
    list-style: none;
}

a {
    text-decoration: none;
}

</style>



