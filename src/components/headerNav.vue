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
                // planetItem: {

                // },
                globalList: [],
                clickedItem: '',

                // componentsList: []


                // characters: [],
                // clickedName: '',
                // planets: [],
                // clickedPlanet: ''
            }
        },
        mounted() {
            fetch("https://swapi.dev/api/?format=json")
            .then(res => res.json())
            .then(data => this.listItems = data)
            .catch(err => console.log(err.message))
            // console.log(this.listItems.data)

        },
        methods: {
                
            async clickOnPeople() {
                const res = await fetch("https://swapi.dev/api/people/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
                // console.table(finalRes.results)
            },

            async clickOnPlanets() {
                // this.componentsList.push(planetsComp);

                const res = await fetch("https://swapi.dev/api/planets/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
                // console.table(componentsList)

                // console.table(finalRes.results)

            }

            


        },

    }


</script>

<!-- characters[] görs till global lista(döper om), beroende på vad man klickar på skickas resultatet in i listan -->


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
        <li v-for="character in globalList">
        <label @click="clickedItem = character.name">{{character.name}}</label>
        <peopleComp v-bind = 'character' v-if = 'character.name == clickedItem' />
        </li>
    </div>

    <!-- <div>
        <li v-for="planets in globalList">
        ><label @click="clickedItem = planets.name">{{planets.name}}</label>
        <planetsComp v-bind = 'planets' v-if = 'planets.name == clickedItem' />
        </li>
    </div> -->
<!-- 
    <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div> -->

    <!-- <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="planet in planets">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div> -->


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



