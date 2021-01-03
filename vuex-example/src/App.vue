<template>
  <div id="app">
    <Header
      :new-message-count="newMessageCount"
    />
    <div class="container mx-auto mt-5">
      <ChatList
        :chat-list="chatList"
      />
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import Header from './components/Header';
import ChatList from './components/ChatList';

import { bus } from './event-bus';

export default {
  name: 'app',
  data() {
    return {
      
    };
  },
  computed: {
    newMessageCount() {
      return this.chatList.map(item => item.new).reduce((a, b) => a + b);
    },
    ...mapState({
      chatList: 'chatList'
    })
  },
  methods: {
  },
  created() {
    bus.$on('CHAT_CLICK', chat => {
      this.readChatItem(chat);
    });
  },
  components: {
    Header,
    ChatList
  },
  mounted() {
    console.log(this.$store);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>