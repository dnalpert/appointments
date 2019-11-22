<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      
      <h1>{{ title }}</h1>
      <appointment-list 
        :appointments="appointments" 
        @remove="removeItem"  
      >
      </appointment-list>
    
    </div>
  </div>

</template>

<script>
import AppointmentList from "./components/AppointmentList"
import _ from "lodash"
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
    AppointmentList
  },
  mounted () {
    axios
    .get("./data/appointments.json")
    .then(response => (this.appointments = response.data))
  },
  methods: {
    removeItem: function (apt) {
      this.appointments = _.without(this.appointments, apt)
    }
  }
};
</script>

<style>
h1 { 
  color: red;
}
</style>
