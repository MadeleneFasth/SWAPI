<script setup>
import swapiVue from './components/swapi.vue';

import ApiURL from './store/apiStorage';


console.log(ApiURL)
</script>

<template>

  <header>
    <h2>SWAPI</h2>

    <nav>
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </nav>

  </header>

  <swapiVue />
</template>


<style>

header {
  background-color: aqua;
}

</style>


