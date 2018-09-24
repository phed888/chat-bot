<template>
    <div class="chat-conversation">
      <div class="chat-container" 
        v-for="(conversation, index) in chat" :key="index"
        v-bind:class="{'attached': conversation.attached}">
        <div class="brand-logo" v-if="conversation.brand && !conversation.attached"></div>
        <div class="time-stamp"
          v-if="!conversation.attached"
          v-bind:class="{'customer': conversation.from == 'customer'}"
        >{{conversation.time}}
        </div>
        <ChatBot v-bind:conversation="conversation" v-on:buttonEvent="addChat($event)"></ChatBot>
      </div>
    </div>
</template>

<script>
import data from "@/data/conversation";
import ChatBot from "@/components/ChatBot";

export default {
  name: "ChatConversation",
  data() {
    return {
      conversations: data,
      chat: [
        {
          time: "12:22 PM",
          attached: false,
          from: "bot",
          brand: "Expedia",
          visibility: true,
          cards: [
            {
              image: false,
              text:
                "Hi, I’m the Expedia bot. I can help you cancel or reconfirm your upcoming booking.",
              buttons: []
            }
          ]
        },
        {
          time: "12:22 PM",
          attached: true,
          from: "bot",
          brand: "Expedia",
          visibility: true,
          cards: [
            {
              image: false,
              text:
                "And if you ask me something I cannot yet help with, I’ll quickly connect you with a friendly customer service agent.",
              buttons: [
                {
                  name: "Upcoming booking",
                  action: "5"
                },
                {
                  name: "Past booking",
                  action: "Past booking"
                },
                {
                  name: "Something else",
                  action: "Something else"
                }
              ]
            }
          ]
        }
      ]
    };
  },
  components: {
    ChatBot
  },
  methods: {
    explode: function({ name, action }) {
      console.log(name + ", " + action);
    },
    showBubble(msg) {
      const self = this;
      self.chat.push(msg);
    },
    addChat({ name, action }) {
      const self = this;
      var custResp = {
        time: "12:22 PM",
        attached: false,
        from: "customer",
        brand: "",
        visibility: true,
        cards: [
          {
            image: false,
            text: name,
            buttons: []
          }
        ]
      };
      setTimeout(this.showBubble, 500, custResp);
      setTimeout(this.showBubble, 1000, self.conversations[action]);
    }
  }
};
</script>

<style>
.attached {
  margin-top: 10px;
}
.chat-conversation {
  background-color: #fff;
  margin: 0 auto;
  padding: 8px;
  width: 375px;
  height: 100vh;
  overflow-x: hidden;
}
.chat-container {
  padding-left: 46px;
  position: relative;
}
.brand-logo {
  position: absolute;
  background-image: url("../assets/logo-expedia.png");
  height: 32px;
  width: 32px;
  top: 20px;
  left: 0;
}
.time-stamp {
  font-size: 11px;
  color: #5b5b5b;
  text-align: left;
  padding-left: 0.5em;
  margin-top: 6px;
}
.time-stamp.customer {
  text-align: right;
  padding-right: 0.5em;
}
.convo-card.cust .time-stamp {
  right: 0;
}
</style>


