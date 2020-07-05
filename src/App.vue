<template>
  <div class="appka">
    <h1> Table of signalers </h1>
    <traffic-state :signaler="signaler"/>
  </div>
</template>

<script>
import trafficState from './components/trafficState.vue';
import { w3cwebsocket as W3CWebSocket } from "websocket";

const wsClient = new W3CWebSocket('ws://localhost:2000');

export default {
    name: 'App',
    components: {
        trafficState
    },
    data: () => {
        return {
        signaler: [],
        connectionStatus: 'Not connected to backend server.'
        }
    },
    methods: {

    },
    created() {
        wsClient.onopen = () => {
          wsClient.send(JSON.stringify({id: 'front'}));
        };

        wsClient.onmessage = (msg) => {
          this.signaler = JSON.parse(msg.data);
        };
        wsClient.onclose = () => {
          // this.signaler = 'conection close...';
        }

    }
}
</script>

<style>
.appka {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background-color: #e9efec;
    float:left;
    width: 100%;
}
</style>
