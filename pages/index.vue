<template>
  <div :style="{ padding: '10px' }">
    <h1>Events Ben</h1>

    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>
<script>
import EventCard from "@/components/EventCard.vue";
import { mapState } from "vuex";
// import EventService from "@/services/EventService.js";
export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: "Event Listing"
    };
  },
  //
  //async asyncData(ctx) {
  //   try {
  //     let response = await EventService.getEvents();
  //     // let response =   await ctx.$axios.get("http://localhost:3000/events");
  //     return {
  //       events: response.data
  //     };
  //   } catch (e) {
  //     ctx.error({ statusCode: 503, message: "server is not online" });
  //   }
  // }

  async fetch(ctx) {
    const { store, error } = ctx;
    try {
      await store.dispatch("events/fetchEvents");
    } catch (e) {
      error({
        statusCode: 503,
        message: "Unable to fetch events at this time. Please try again."
      });
    }
  },

  computed: mapState({
    events: state => state.events.events
  })
};
</script>
