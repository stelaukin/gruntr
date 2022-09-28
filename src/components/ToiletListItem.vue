<template>
  <!-- Displays search results including toilet name, address and a button to leave a review !not working -->
  <p class="reviewList">
    Toilet Name: {{ name }} <br />Address: {{ address }} <br /><button
      @click="warnDisabled"
    >
      Leave Review
    </button>
    <span v-if="disabled"> Sorry, this feature is under development!</span>
  </p>
</template>

<script>
export default {
  props: {
    name: String,
    address: String,
  },
  data() {
    return {
      disabled: false,
    };
  },
  methods: {
    warnDisabled() {
      this.disabled = true;
      setTimeout(() => {
        this.disabled = false;
      }, 1500);
    },
  },
};
</script>

<style scoped>
.reviewList {
  padding: 5px;
  background-color: #804815;
  border: 1px;
  border-style: solid;
  width: 60%;
  border-color: rgb(155, 64, 4);
  font-size: 20px;
  text-align: center;
  color: rgb(228, 206, 186);
  border-radius: 25px;
  box-shadow: 5px 5px rgba(19, 75, 17, 0.74);
}
</style>