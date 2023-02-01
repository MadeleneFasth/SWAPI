<script>
import { VueElement } from 'vue';
import undernav from './undernav.vue';


  export default {
    components: {
        undernav
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
            // doThisOnClick() {
            //     fetch("https://swapi.dev/api/people/?format=json")
            //     .then(res => res.json())
            //     .then(data => this.Item = data)
            //     .catch(err => console.log(err.message))
            //     console.table(this.Item)
                
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

    <div>
        <!-- <li v-for="(a, b) in item">
        >{{b}}
        </li> -->

        <li v-for="character in characters">
        ><label @click="clickedName = character.name">{{character.name}}</label>
        <undernav v-bind = 'character' v-if = 'character.name == clickedName' />
        </li>
    </div>
<!-- 
    <p v-for="name in Items">
{{ name }}
    </p> -->


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



