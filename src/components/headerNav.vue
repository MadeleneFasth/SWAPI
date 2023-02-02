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

                filmsList: [],

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
                this.filmsList = []
            },

            async clickOnFilms() {
                console.log('hej')
                let thisComp = filmsComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/films/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.filmsList = finalRes.results;
                this.globalList = []
            },

            async clickOnSpecies() {
                let thisComp = speciesComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/species/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
                this.filmsList = []
            },

            async clickOnVehicles() {
                let thisComp = vehiclesComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/vehicles/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
                this.filmsList = []
            },

            async clickOnStarships() {
                let thisComp = starshipsComp;
                this.comp = thisComp;
                const res = await fetch("https://swapi.dev/api/starships/?format=json");
                const finalRes = await res.json();
                this.item = finalRes;
                this.globalList = finalRes.results;
                this.filmsList = []
            }
        }

    }


</script>

<!-- characters[] görs till global lista(döper om), beroende på vad man klickar på skickas resultatet in i listan -->


<template>
    <header>
        <img src="../assets/starvarsSVGloggo.svg"/>
        <h2>The only Star Wars dictionary you'll ever need</h2>
        <h3>The only Star Wars dictionary you'll ever need</h3>
        <nav>
            <ul class="nav-ul">
                <li class="nav-list" @click="clickOnPeople">People</li>
                <li class="nav-list" @click="clickOnPlanets">Planets</li>
                <li class="nav-list" @click="clickOnFilms">Films</li>
                <li class="nav-list" @click="clickOnSpecies">Species</li>
                <li class="nav-list" @click="clickOnVehicles">Vehicles</li>
                <li class="nav-list" @click="clickOnStarships">Starships</li>
            </ul>
        </nav>
    </header>


<div class="sub_category">
    <li v-for="item in globalList">
            <label @click="clickedItem = item.name ">{{item.name}}</label>
            <component :is="comp" v-bind = 'item' v-if = 'item.name == clickedItem'/>
    </li>


    <li v-for="item in filmsList">
        <label @click="clickedItem = item.title ">{{item.title}}</label>
        <component :is="comp" v-bind = 'item' v-if = 'item.title == clickedItem'/>
    </li>
</div>

</template>


<style>

body {
    position: relative;
}

body {
    position: relative;
}


/* button {
    min-width: 10rem;
    background-color: white;
    border: none;
    padding: 1rem;
    margin: 1rem; 
    text-align: center;
    text-decoration: none;
} */

/* nav {
    background-color:  #B3B3B3;
    display: flex;
    justify-content: space-around;
    align-items: flex-end;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-content: center;
    align-items: center;
    min-height: 10em;
} */

header {
    background-color: black;
    background-image: url(../assets/backgroundStars.png);
}

header h2 {
    font-weight: lighter;
    color: #ffe81fff;
}

.nav-ul {
    /* background-color:  #B3B3B3; */
    display: flex;
    justify-content: space-around;
    height: 4em;
    /* align-items: flex-end; */
    /* flex-wrap: wrap; */
    /* justify-content: space-evenly; */
    /* align-content: center; */
    /* align-items: center; */
    /* min-height: 10em; */
}

.nav-list {
    font-family: 'Righteous', cursive;
    color: #ffe81fff;
    list-style: none;
    border: .5px solid #ffe81fff;
    flex: 1 1 100%;
    text-align: center;
}

.sub_category li {
    font-family: 'Righteous', cursive;
    min-height: 4rem;
    max-width: 10rem;
    margin: 1rem;
    list-style: none;
    display: flex;
    justify-content: center;
    align-items: center;

    border: 4px solid #ffe81fff;
    background-color: transparent; 
    
}

label {
    color: #ffe81fff;
}

.sub_category {
    min-height: 800px;
    padding: 1rem;
    background-color: transparent;
}

.card {
    height: 500px;
    width: 500px;
    padding: 2rem;

    position: absolute;
    left: 50%;
    margin-left: -250px;
    top: 50%;
    margin-top: -250px;

    /* 
    right: 0; 
    top: 0;
    margin: 8em 12em 12em 12em; */

    border: 4px solid #ffe81fff;
    color: #ffe81fff;
    background-color: transparent;
}

a {
    text-decoration: none;
}


</style>