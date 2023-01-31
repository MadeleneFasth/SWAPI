<script>
  export default {
    data() {
      return {
        listItems: []
      }
    },
    methods: {
      async getData() {
        const res = await fetch("https://swapi.dev/api/?format=json");
        const finalRes = await res.json();
        this.listItems = finalRes;
      }
    },
    mounted() {
      this.getData()
    }
}


fetch('https://swapi.dev/api/?format=json')
.then(response => response.json())
.then(response => console.table(response))

</script>


<template>
    <div v-for="(item, index) in listItems">
      <a v-bind:href="item">{{index}}</a>
    </div>
  </template>

<!-- 
<style>

</style> -->