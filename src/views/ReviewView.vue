<!-- SEARCH FOR AND FILTER LIST -->

<template>
  <div>
    <h1>Search for a Gruntr</h1>
    <h3>Search</h3>

    <!-- User input to search public toilets -->
    <input
      v-model="input"
      style="font-size: larger"
      placeholder="find a gruntr"
    />
    <p>Search results: {{ search }}</p>

    <!-- Will filter list of toilets based on user search -->
    <div v-for="toilet in filteredToilets" v-bind:key="toilet.FacilityID">
      <!-- Displays search results including toilet name, address and a button to leave a review (not working) -->
      <ToiletListItem :name="toilet.Name" :address="toilet.Address1" :town="toilet.Town"/>
      <br />
    </div>
  </div>
</template>

<!-- don't write to Json file, simplest way local storage (cookie) mdn webdoc, -->

<style>
/* Animations for review on button click - 'in development' */
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
</style>

<script>
// import toilet data
import rawToilets from "../assets/data/toiletsTas.json";
import { defineComponent, ref } from "vue";
// import prop for displaying toilets that are searched
import ToiletListItem from "../components/ToiletListItem.vue";


export default defineComponent({
  data() {
    return {
      // toilet data from json file
      toilets: rawToilets,
      search: "",

      toSearch: "Please Enter the Name of a Public Toilet",
      show: true,
      input: "",
      filteredToilets: rawToilets,
    };
  },
  // Prop for displaying toilets in search
  components: { ToiletListItem },


  // Watcher to update list of toilets based on search input
  watch: {
    input: function (newInput, oldInput) {
      if (newInput == "") {
        this.filteredToilets = this.toilets;
        return;
      }
      this.filteredToilets = this.toilets.filter((toilet) => {
        return (
          toilet.Name.toLowerCase().indexOf(newInput.toLowerCase()) > -1 ||
          toilet.Town.toLowerCase().indexOf(newInput.toLowerCase()) > -1 ||
          toilet.Address1.toLowerCase().indexOf(newInput.toLowerCase()) > -1
        );
      });
      console.log(newInput + oldInput);
    },
  },


  // returns toilet list - matches with search
  // computed: {
  //   filteredToilets() {
  //     return this.toilets.filter((toilet) => {
  //       return (
  //         toilet.Name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
  //       );
  //     });
  //   },
  // },
});
</script>
