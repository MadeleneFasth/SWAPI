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
                people: [],
                clickedName: '',

                planets: [],
                clickedPlanet: '',

                films: [],
                clickedFilm: '',
                
                species: [],
                clickedSpecies: '',

                vehicles: [],
                clickedVehicle: '',
                
                starships: [],
                clickedStarship: ''
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
                this.characters = finalRes.results;
            },

            async clickOnPlanets() {
                const res = await fetch("https://swapi.dev/api/planets/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.planets = finalRes.results;
            },

            async clickOnFilms() {
                const res = await fetch("https://swapi.dev/api/films/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.films = finalRes.results;
            },

            async clickOnSpecies() {
                const res = await fetch("https://swapi.dev/api/species/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.species = finalRes.results;
            },

            async clickOnVehicles() {
                const res = await fetch("https://swapi.dev/api/vehicles/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.vehicles = finalRes.results;
            },

            async clickOnStarships() {
                const res = await fetch("https://swapi.dev/api/starships/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.starships = finalRes.results;
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
        <li v-for="person in people">
        <label @click="clickOnPeople = person.name">{{person.name}}</label>
        <peopleComp v-bind = 'person' v-if = 'person.name == clickedName' />
        </li>
    </div>

    <div>
        <li v-for="planet in planets">
        ><label @click="clickOnPlanets = planet.name">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planets.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="film in films">
        ><label @click="clickOnFilms = film.name">{{film.name}}</label>
        <filmsComp v-bind = 'film' v-if = 'film.name == clickedFilm' />
        </li>
    </div>

    <div>
        <li v-for="specie in species">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <speciesComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="vehicle in vehicles">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <vehiclesComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="starship in starships">
        ><label @click="clickedPlanet = planet.name">{{planet.name}}</label>
        <starshipsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
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



