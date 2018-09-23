<template>
  <div class="card-carousel">
    <ChatBot v-bind:conversations="conversations.PostCards"/>
  </div>
</template>

<script>
import data from '@/data/conversation';

export default {
  name: 'Carousel',
  data() {
    return {
      conversations: data
    };
  }
};
</script>

<style>
.card-carousel {
  display: flex;
}
</style>
