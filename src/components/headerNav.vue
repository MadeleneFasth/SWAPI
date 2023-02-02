<script>
import { VueElement } from 'vue';
import peopleComp from './peopleComp.vue';
import planetsComp from './planetsComp.vue';
import filmsComp from './filmsComp.vue';
import speciesComp from './speciesComp.vue';
import vehiclesComp from './vehiclesComp.vue';
import starshipsComp from './starshipsComp.vue';


  export default {
    components: {
        peopleComp,
        planetsComp,
        filmsComp,
        speciesComp,
        vehiclesComp,
        starshipsComp
    },
        data() {
            return {

                listItems: [],
                item: {}, 

                globalList: [],
                clickedItem: '',

                comp: []

            }
        },
        mounted() {
            fetch("https://swapi.dev/api/?format=json")
            .then(res => res.json())
            .then(data => this.listItems = data)
            .catch(err => console.log(err.message))

        },
        methods: {
                
            async clickOnPeople() {
                console.log('hej')
                let thisComp = peopleComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/people/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            },

            async clickOnPlanets() {
                let thisComp = planetsComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/planets/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            },

            async clickOnFilms() {
                console.log('hej')
                let thisComp = filmsComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/films/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            },

            async clickOnSpecies() {
                let thisComp = speciesComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/species/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            },

            async clickOnVehicles() {
                let thisComp = vehiclesComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/vehicles/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            },

            async clickOnStarships() {
                let thisComp = starshipsComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/starships/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
            }
        }

    }


</script>

<!-- characters[] görs till global lista(döper om), beroende på vad man klickar på skickas resultatet in i listan -->


<template>
    <h1>SWAPI</h1>
    <p>The Star Wars API</p>
    <nav>
        <button @click="clickOnPeople">People</button>
        <button @click="clickOnPlanets">Planets</button>
        <button @click="clickOnFilms">Films</button>
        <button @click="clickOnSpecies">Species</button>
        <button @click="clickOnVehicles">Vehicles</button>
        <button @click="clickOnStarships">Starships</button>
    </nav>

<div>
    <li v-for="item in globalList">
        <label @click="clickedItem = item.name ">{{item.name}}</label>
        
        <component :is="comp" v-bind = 'item' v-if = 'item.name == clickedItem'/>
    </li>

    <li v-for="item in globalList">
        <label @click="clickedItem = item.title ">{{item.title}}</label>
        
        <component :is="comp" v-bind = 'item' v-if = 'item.title == clickedItem'/>
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



