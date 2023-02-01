<script>
import { VueElement } from 'vue';
import peopleComp from './peopleComp.vue';
import planetsComp from './planetsComp.vue';


  export default {
    components: {
        peopleComp,
        planetsComp
    },
        data() {
            return {
                listItems: [],
                item: {
                }, 
                planetItem: {

                },


                characters: [],
                clickedName: '',
                planets: [],
                clickedPlanet: ''
            }
        },
        mounted() {
            fetch("https://swapi.dev/api/?format=json")
            .then(res => res.json())
            .then(data => this.listItems = data)
            .catch(err => console.log(err.message))
            console.log(this.listItems.data)

        },
        methods: {
                
            async clickOnPeople() {
                const res = await fetch("https://swapi.dev/api/people/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.characters = finalRes.results;
                // console.table(finalRes.results)
            },

            async clickOnPlanets() {
                const res = await fetch("https://swapi.dev/api/planets/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.planets = finalRes.results;
                // console.table(finalRes.results)
            }

    }


</script>




<template>

    <nav>
        <button @click="clickOnPeople">People</button>
        <button @click="clickOnPlanets">Planets</button>
        <button @click="clickOnFilms">Films</button>
        <button @click="clickOnSpecies">Species</button>
        <button @click="clickOnVehicles">Vehicles</button>
        <button @click="clickOnStarships">Starships</button>
    </nav>

    <div>
        <li v-for="character in characters">
        ><label @click="clickedName = character.name">{{character.name}}</label>
        <peopleComp v-bind = 'character' v-if = 'character.name == clickedName' />
        </li>
    </div>
    
    <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>


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



