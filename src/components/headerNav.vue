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

                pageCount: 2,

                listItems: [],
                item: {},

                globalList: [],
                clickedItem: '',

                filmsList: [],

                comp: []

            }
        },
 
        methods: {

            async clickFetch(comp, url, isFilmCategory) { //default för parameter är undefined
                this.comp = comp;
                const res = await fetch(url);
                const finalRes = await res.json();
                this.item = finalRes;
                if(isFilmCategory) {
                    this.filmsList = finalRes.results;
                    this.globalList = []
                } else {
                    this.globalList = finalRes.results;
                    this.filmsList = []
                }
            },
                
            async clickOnPeople() {
                this.clickFetch(peopleComp, "https://swapi.dev/api/people/?format=json")
            },

            async clickOnPlanets() {
                this.clickFetch(planetsComp, "https://swapi.dev/api/planets/?format=json")
            },

            async clickOnFilms() {
                let isFilmCategory = true;
                this.clickFetch(filmsComp, "https://swapi.dev/api/films/?format=json", isFilmCategory)

            },

            async clickOnSpecies() {
                this.clickFetch(speciesComp, "https://swapi.dev/api/species/?format=json")
            },

            async clickOnVehicles() {
                this.clickFetch(vehiclesComp, "https://swapi.dev/api/vehicles/?format=json")
            },

            async clickOnStarships() {
                this.clickFetch(starshipsComp, "https://swapi.dev/api/starships/?format=json")
            },

            onNxtBtnClick() {
                this.clickFetch(this.comp, this.item.next);
            },

            onPrevBtnClick() {
                this.clickFetch(this.comp, this.item.previous)
            }
        }
    }
</script>


<template>
    <header>
        <img src="../assets/starvarsSVGloggo.svg"/>
        <h2>The only Star Wars dictionary you'll ever need</h2>
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
        <button class="header-btn-prev" @click="onPrevBtnClick">previous</button>
        <button class="header-btn-nxt" @click="onNxtBtnClick">next</button>
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

.header-btn-prev, 
.header-btn-nxt {
    font-family: 'Righteous', cursive;
    text-align: center;
    padding: 0.5rem;
    margin: 0.5rem;
    color:#ffe81fff ;

    border: 2px solid #ffe81fff;
    background-color: transparent; 
    box-shadow: 2px 2px 5px  #ffe81fff;
}

body {
    position: relative;
    background-image: url(../assets/backgroundStars.png);
}

header {
padding-top: 3em;
}

header img {
padding-left: 1em;
}

header h2 {
    font-weight: lighter;
    color: #ffe81fff;
    padding: .5em 0em 1em 1em;
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
    font-size: 2rem;
    color: #ffe81fff;
    list-style: none;

    border: .5px solid #ffe81fff;

    display: flex;
    flex: 1 1 100%;
    justify-content: center;
    align-items: center;
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
    box-shadow: 2px 2px 5px  #ffe81fff;
    
}

label {
    color: #ffe81fff;
    text-align: center;
}

.sub_category {
    min-height: 800px;
    padding: 1rem;
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
    box-shadow: 2px 2px 6px #ffe81fff;
}

a {
    text-decoration: none;
}


</style>