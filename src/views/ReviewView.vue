<!-- SEARCH FOR AND FILTER LIST -->

<template>
  <div>
    <h1>Search for a Gruntr</h1>
    <h3>Search</h3>

    <!-- User input to search public toilets -->
    <input v-model="search" placeholder="find a gruntr" />
    <p>Search results: {{ search }}</p>

    <!-- Will filter list of toilets based on user search -->
    <div v-for="toilet in filteredToilets" v-bind:key="toilet.Name">
      <!-- Displays search results including toilet name, address and a button to leave a review !not working -->
      <p class="reviewList">
        {{ toilet.Name }} | {{ toilet.Address1 }}
        <button @click="warnDisabled">Leave Review</button>
        <span v-if="disabled"> Sorry, this feature is under development!</span>
      </p>
      <br>
    </div>
  </div>
</template>

<!-- don't write to Json file, simplest way local storage (cookie) mdn webdoc, -->

<style>
/* Animations for warning on button click - 'in development' */
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.shake {
  animation: shake 0.82s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
  transform: translate3d(0, 0, 0);
}

@keyframes shake {
  10%,
  90% {
    transform: translate3d(-1px, 0, 0);
  }

  20%,
  80% {
    transform: translate3d(2px, 0, 0);
  }

  30%,
  50%,
  70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%,
  60% {
    transform: translate3d(4px, 0, 0);
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.reviewList {
  padding: 5px;
  background-color: #804815;
  border: 1px;
  border-style: solid;
  width: fit-content;
  border-color: rgb(155, 64, 4);
  font-size: 20px;
  text-align: center;
  color: rgb(228, 206, 186);

}
</style>

<script>
// import toilet data
import rawToilets from "../assets/data/toiletsTas.json";
import { defineComponent, ref } from "vue";
export default defineComponent({
  data() {
    return {
      toilets: rawToilets,
      search: "",
      disabled: false,
      toSearch: "Please Enter the Name of a Public Toilet",
      show: true,
    };
  },
  // displays warning when trying to leave review
  methods: {
    warnDisabled() {
      this.disabled = true;
      setTimeout(() => {
        this.disabled = false;
      }, 1500);
    },
  },
  // returns toilet list - matches with search
  computed: {
    filteredToilets() {
      return this.toilets.filter((toilet) => {
        return (
          toilet.Name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
        );
      });
    },
  },
});
</script>
