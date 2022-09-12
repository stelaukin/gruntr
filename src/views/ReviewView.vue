<!-- SEARCH FOR AND FILTER LIST -->

<template>
  <div>
    <h1>Search for a Gruntr</h1>
    <h3>Search</h3>
    <!-- User input to search public toilets -->
    <input v-model="search" placeholder="find a gruntr" />
    <p>Search results: {{ search }}</p>

    <div v-for="toilet in filteredToilets" v-bind:key="toilet.Name">
      <p>{{ toilet.Name }} </p>
    </div>

    <!-- <ul>
      <li v-for="toilet in toilets" v-bind:key="toilet.FacilityID">
        {{ toilet.Name }}
      </li>
    </ul> -->
    <p>display search result here:</p>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

<script>
import rawToilets from "../assets/data/toiletsTas.json";
import { defineComponent } from "vue";
export default defineComponent({
  data() {


    return {
      toilets: rawToilets,
      search: "",
    };
  
  },

  computed: {
    filteredToilets() {
      return this.toilets.filter(toilet => {
         return toilet.Name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
    }
  },
});
</script>
  