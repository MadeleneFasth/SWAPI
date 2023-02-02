<script>
import { VueElement } from 'vue';
import peopleComp from './peopleComp.vue';
import planetsComp from './planetsComp.vue';
import filmsComp from './filmsComp.vue';
// import speciesComp from './.vue'
import vehiclesComp from './vehiclesComp.vue'
import starshipsComp from './starshipsComp.vue'
//import all components

  export default {
    components: {
        peopleComp,
        planetsComp,
        filmsComp,
        // speciesComp,
        vehiclesComp,
        starshipsComp
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
                
                // species: [],
                // clickedSpecies: '',

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
                console.log('people clicked');
                const res = await fetch("https://swapi.dev/api/people/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.people = finalRes.results;
            },

            async clickOnPlanets() {
                console.log('planet clicked');
                const res = await fetch("https://swapi.dev/api/planets/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.planets = finalRes.results;
            },

            async clickOnFilms() {
                console.log('film clicked');
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
            }, 
            
            selectClickedName(newClicked, category) {
            // reset all names
            if(category == "planet") this.clickedPlanet = newClicked;
            console.log('selectClickedName funktionen kör')
            this.clickedPlanet = category == "planet" ? newClicked : '';
            },
        }
    }


</script>

<!-- characters[] görs till global lista(döper om), beroende på vad man klickar på skickas resultatet in i listan -->


<template>
<header>
    <h1>SWAPI</h1>
    <p>The Star Wars API</p>
</header>
    <nav>
        <button @click="clickOnPeople">People</button>
        <button @click="clickOnPlanets">Planets</button>
        <button @click="clickOnFilms">Films</button>
        <button @click="clickOnSpecies">Species</button>
        <button @click="clickOnVehicles">Vehicles</button>
        <button @click="clickOnStarships">Starships</button>
    </nav>

    <div class="sub_categories">
        <li v-for="person in people">
        <label @click="clickedName = person.name">{{person.name}}</label>
        <peopleComp v-bind = 'person' v-if = 'person.name == clickedName' />
        </li>
    </div>

    <div>
        <li v-for="planet in planets">
        <!-- <label @click="clickedPlanet = planet.name">{{planet.name}}</label> -->
        <label @click="() => selectClickedName(planet.name, 'planet')">{{planet.name}}</label>
        <planetsComp v-bind = 'planet' v-if = 'planet.name == clickedPlanet' />
        </li>
    </div>

    <div>
        <li v-for="film in films">
        <label @click="clickedFilm = film.name">{{film.name}}</label>
        <filmsComp v-bind = 'film' v-if = 'film.name == clickedFilm' />
        </li>
    </div>

    <!-- <div>
        <li v-for="specie in species">
        ><label @click="clickedSpecies = specie.name">{{specie.name}}</label>
        <speciesComp v-bind = 'specie' v-if = 'specie.name == clickedSpecies' />
        </li>
    </div> -->

    <div>
        <li v-for="vehicle in vehicles">
        <label @click="clickedVehicle = vehicle.name">{{vehicle.name}}</label>
        <vehiclesComp v-bind = 'vehicle' v-if = 'vehicle.name == clickedVehicle' />
        </li>
    </div>

    <div>
        <li v-for="starship in starships">
        <label @click="clickedStarship = starship.name">{{starship.name}}</label>
        <starshipsComp v-bind = 'starship' v-if = 'starship.name == clickedStarship' />
        </li>
    </div>

</template>


<style>
header {
    display: flex;
    justify-content: center;
    flex-direction: column;

    text-align: center;
    font-family:Arial, Helvetica, sans-serif;
    background-color: #CABEBE;
    min-height: 10rem;
}
nav {
    background-color:  #B3B3B3;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-content: center;
    align-items: center;
    min-height: 10em;
}

button {
    min-width: 15rem;
    background-color:#E6E6E6;
    border: none;
    padding: 15px 32px;
    text-decoration: none;
    font-size: 16px;
}

.sub_categories {
    padding: 1rem;
    background-color: #808080;
}

li {
    margin: 1rem;
    list-style: none;
}

a {
    text-decoration: none;
}

</style>



