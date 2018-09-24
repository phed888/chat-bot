<template>
  <div class="card-container" v-bind:class="{'customer': conversation.from == 'customer'}">
    <div class="card convo-card"
      v-for="(card, index) in conversation.cards" :key="index"
      v-bind:class="{'carousel': card.image.length, 'attached': card.attached}">
        <div class="card-image" v-if="card.image.length">
          <img :src="getImgUrl(card.image)" alt="" />
        </div>
        <div class="card-text">{{card.text}}</div>
        <div class="card-buttons" v-if="card.buttons.length">
          <button class="btn-chat" 
            v-for="(button, index) in card.buttons" :key="index"
            v-on:click="doAction(button.name, button.action)">{{button.name}}</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatBot",
  data() {
    return {};
  },
  props: ["conversation"],
  methods: {
    getImgUrl(img) {
      var image = require("../assets/photos/" + img + ".png");
      return image;
    },
    doAction(name, action) {
      this.$emit("buttonEvent", { name, action });
    }
  }
};
</script>

<style>
.card-container {
  display: flex;
  width: 100%;
}
.customer {
  justify-content: flex-end;
}
.card-container .card {
  margin-right: 20px;
  display: block;
}
.card-container .card:last-child {
  margin-right: 0;
}
.card-image {
  border-radius: 13px 13px 0 0;
  overflow: hidden;
}
.carousel {
  min-width: 240px !important;
}
.convo-card {
  border-radius: 14px;
  background-color: #eaeaea;
  border: none;
  color: #5b5b5b;
  padding: 0;
  position: relative;
  min-width: 130px;
  max-width: 85%;
}
.card-container.customer .convo-card {
  background-color: #00365f;
  color: white;
}
.card-text {
  padding: 16px;
  text-align: left;
}
.card-buttons {
  /* border-radius: 0 0 13px 13px; */
  /* box-shadow: rgba(0, 0, 0, 0.2) 0px 2px 4px 0px; */
  margin: 0 1px 2px 2px;
}
.btn-chat {
  border: none;
  background-color: #fff;
  border-radius: 0;
  color: #2864d7;
  height: 48px;
  padding: 0 0 0 16px;
  text-align: left;
  width: calc(100% - 2px);
  margin-bottom: 2px;
}
.btn-chat:last-child {
  border-radius: 0 0 13px 13px;
  margin-bottom: 0;
}
</style>


