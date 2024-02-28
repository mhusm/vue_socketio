
<script setup>
import { state, socket } from "@/socket";
import { ref } from 'vue'

const name = ref('')

function sendEvent(event) {
  socket.emit("name", name.value);
}

</script>
<template>
  <p>State: {{ connected }}</p>
  <input type="text" v-model="name" />
  <button @click="sendEvent">Send my name</button>
  <p>The server says</p>
  <p>{{ serverMessage }}</p>
</template>
  
<script>
import { state, socket } from "@/socket";

export default {
  name: "ConnectionState",

  computed: {
    connected() {
      return state.connected;
    },
    serverMessage() {
      return state.serverMessage;
    }

  }
}

</script>