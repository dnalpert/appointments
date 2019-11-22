<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      
      <h1>{{ title }}</h1>
      <appointment-list :appointments="appointments"></appointment-list>
    
    </div>
  </div>

</template>

<script>
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome"
import AppointmentList from "./components/AppointmentList"
import axios from "axios"

export default {
  name: "MainApp",
  data: function() {
    return {
      title: "Appointment List",
      appointments: []
    };
  },
  components: {
    // FontAwesomeIcon,
    AppointmentList
  },
  mounted () {
    axios
    .get("./data/appointments.json")
    .then(response => (this.appointments = response.data))
  }
};
</script>

<style>
h1 { 
  color: red;
}
</style>
