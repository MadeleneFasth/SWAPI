<script>
import card from './card.vue';
import headerNav from './headerNav.vue'

  export default {
    components: {
        card, 
        headerNav
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
    <div>
        <li v-for="character in characters">
        ><label @click="clickedName = character.name">{{character.name}}</label>
        <card v-bind = 'character' v-if = 'character.name == clickedName' />
        </li>
    </div>


</template>