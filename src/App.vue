<template>
  <div id="main-app" class="container">
    <h1>{{ title }}</h1>
    <font-awesome-icon icon="plus" class="mr-2"/>Add New Appointment
  </div>

</template>

<script>
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome"

export default {
  name: 'MainApp',
  data: function() {
    return {
      title: 'Appointment List'
    }
  },
  components: {
    FontAwesomeIcon
  }
}
</script>

<style>

</style>
