<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      
      <h1>{{ title }}</h1>
      <add-appointment
        @add="addItem"  
      ></add-appointment>
      <appointment-list 
        :appointments="appointments" 
        @remove="removeItem"
        @edit="editItem"  
      >
      </appointment-list>
    </div>
  </div>

</template>

<script>
import AppointmentList from "./components/AppointmentList";
import AddAppointment from "./components/AddAppointment";
import _ from "lodash";
import axios from "axios";

export default {
  name: "MainApp",
  data: function() {
    return {
      title: "Appointment List",
      appointments: [],
      aptIndex: 0
    };
  },
  components: {
    AppointmentList,
    AddAppointment
  },
  mounted () {
    axios
    .get("./data/appointments.json")
    .then(response => (this.appointments = response.data.map(item => {
      item.aptId = this.aptIndex;
      this.aptIndex++;
      return item;
    })))
  },
  methods: {
    removeItem: function (apt) {
      this.appointments = _.without(this.appointments, apt);
    },
    editItem: function (id, field, text) {
      const aptIndex = _.findIndex(this.appointments, {
        aptId: id
      });
      this.appointments[aptIndex][field] = text;
    },
    addItem: function (apt) {
      apt.aptId= this.aptIndex;
      this.aptIndex++;
      this.appointments.push(apt)
    }
  }
};
</script>

<style>
h1 { 
  color: red;
}
</style>
