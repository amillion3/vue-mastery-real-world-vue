<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <!-- `event` is passed as a prop to EventCard -->
  </div>
</template>

<script>
import EventCard from "../components/EventCard.vue";
import EventService from "../services/EventService.js";

export default {
  components: {
    EventCard,
  },
  data() {
    return {
      events: [],
    };
  },
  created() {
    EventService.getEvents().then((response) => {
      this.events = response.data;
    });
  },
};
</script>

<style></style>
