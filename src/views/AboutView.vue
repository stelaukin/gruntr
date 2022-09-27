<!-- Create an account form - not fully implemented -->
<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>Email: </label>
      <input type="email" v-model="email" required /><br>

      <label>Password: </label>
      <input type="password" v-model="password" required /><br>
      <div v-if="passwordError" class="error">{{ passwordError }}</div>

      <label>Role: </label>
      <select v-model="role">
        <option value="parent">Parent</option>
        <option value="transport">Transport</option>
        <option value="grey">Grey Nomad</option>
      </select>

      <div  class="checkboxes">
        <input type="checkbox" value="car" v-model="vehicle" />
        <label>Car</label>
        <input type="checkbox" value="truck" v-model="vehicle" />
        <label>Truck</label>
        <input type="checkbox" value="caravan" v-model="vehicle" />
        <label>Caravan</label>
      </div>

      <div  class="checkboxes">
        <input type="checkbox" v-model="terms" required />
        <label>Please accept terms and conditions</label>
      </div>
      <div class="button">
        <button class="submit" type="submit">Sign up here</button>
      </div>
    </form>

    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>
      Vehicle: <span v-for="veh in vehicle" :key="veh"> {{ veh }}</span>
    </p>
    <p>Terms : {{ terms }}</p>
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
.checkboxes {
  text-align:left;
}

.checkboxes input{
  margin: 0px 4px 2px 0px;
}

.checkboxes label{
  margin: 0px 20px 0px 3px;
}
</style>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "what describes you best",
      vehicle: [],
      terms: false,
      passwordError: "",
    };
  },
  
  methods: {
    handleSubmit() {
      //Validate password field length
      this.passwordError =
        this.password.length > 6
          ? ""
          : "Password must be more than 6 characters long!";

    },
  },
};
</script>
