<template>
  <div>
    <h1>Event List</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from '@/services/EventService.js';

export default {
    components: {
        EventCard
    },
    data() {
        return {
            events: []
        }
    },
    created() {
        EventService.getEvents()
        .then(resp => {
            this.events = resp.data
            console.log(resp.data);
        })
        .catch(err => {
            console.log('There was a error' + err.resp);
        })
    }
};
</script>
