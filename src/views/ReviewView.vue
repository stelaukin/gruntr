

<template>
  <div>
    <p>poop</p>
    <h3>Search</h3>
    <p>Message is: {{ message }}</p>
<input v-model="message" placeholder="edit me" />
    <!-- <p v-if="search.length <= 8">Password: must be 8 characters</p>
    <p v-else>Password: {{ search }}</p> --> -->
    <h1>This is a reviews page</h1>
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
      };
    },
    data() {
    return {
      message: ''
    }
  }
  })

  </script>
  