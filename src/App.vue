/* eslint-disable no-console */
/* eslint-disable no-console */
<template>
  <div id="app">
    <div class="main">
      <div class="calendar-holder">
        <calendar :events="events" />
      </div>
      <div class="form-holder">
        <h3>Schedule an event</h3>
        <event-form  @fetch-events='fetchEvents()'/>
      </div>
    </div>
  </div>
</template>

<script>
import Calendar from './components/Calendar.vue'
import EventForm from './components/EventForm.vue'
import axios from 'axios';
export default {
  name: 'app',
  components: {
    Calendar,
    EventForm
  },
  data(){
    return {
      events: []
    }
  },
  mounted: async function () {
       await this.fetchEvents();
  },
  methods: {
      async fetchEvents () {
        axios
      .get('http://localhost:3000/events')
      .then(response => (this.events = response.data))
      },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  display: flex;
  align-items: center;
}
.calendar-holder {
  width: 65%;
}
.form-holder {
  width: 35%;
}

.form-holder > h3 {
  color: orangered;
  text-transform: uppercase;
  font-size: 16px;
  text-align: left;
  margin-left: 30px;
  margin-bottom: 10px;
}
</style>
