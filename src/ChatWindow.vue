<template>
  <div class="sc-chat-window" :class="{opened: isOpen, closed: !isOpen}">
    <Header
      :teamName="agentProfile.teamName"
      :imageUrl="agentProfile.imageUrl"
      :onClose="onClose"
      :mainColor="mainColor"
      :isTyping="isTyping"
    />
    <MessageList
      :messages="messageList"
      :imageUrl="agentProfile.imageUrl"
      :chatImageUrl="agentProfile.imageUrl"
      :mainColor="mainColor"
      v-if="!video"
    />
    <div id="video" class="sc-video" v-else> 
        <div id="subscriber"></div>
        <div id="publisher"></div>
    </div>
    <UserInput :showEmoji="showEmoji" :onSubmit="onUserInputSubmit" :showFile="showFile" :placeholder="placeholder"/>
  </div>
</template>

<script>
import Header from './Header.vue'
import MessageList from './MessageList.vue'
import UserInput from './UserInput.vue'

export default {
  components: {
    Header,
    MessageList,
    UserInput
  },
  props: {
    'showEmoji': {
      type: Boolean,
      default: false
    },
    'showFile': {
      type: Boolean,
      default: false
    },
    'agentProfile': {
      type: Object,
      required: true
    },
    'onUserInputSubmit': {
      type: Function,
      required: true
    },
    'onClose': {
      type: Function,
      required: true
    },
    'messageList': {
      type: Array,
      default: () => []
    },
    'isOpen': {
      type: Boolean,
      default: () => false
    },
    placeholder: {
      type: String,
      default: "Write a reply"
    },
    mainColor: {
      type: String,
      default: "blue"
    },
    isTyping: {
      type: Boolean,
      default: false
    },
    video: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {

    }
  },
  methods: {
  }
}
</script>
<style scoped>
.sc-chat-window {
  width: 370px;
  height: calc(100% - 120px);
  max-height: 590px;
  position: fixed;
  right: 25px;
  bottom: 100px;
  box-sizing: border-box;
  box-shadow: 0px 7px 40px 2px rgba(148, 149, 150, 0.3);
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: 0.3s ease-in-out;
  border-radius: 10px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}

.sc-chat-window.closed {
  opacity: 0;
  visibility: hidden;
  bottom: 90px;
}

.sc-message--me {
  text-align: right;
}
.sc-message--them {
  text-align: left;
}
.sc-video {
  position: relative;
  width: 100%;
  height: 100%;
  margin-left: auto;
  margin-right: auto;
}

@media (max-width: 450px) {
  .sc-chat-window {
    width: 100%;
    height: 100%;
    max-height: 100%;
    right: 0px;
    bottom: 0px;
    border-radius: 0px;
  }
  .sc-chat-window {
    transition: 0.1s ease-in-out;
  }
  .sc-chat-window.closed {
    bottom: 0px;
  }
}
#subscriber {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 10;
}

#publisher {
  position: absolute;
  border: 2px solid white;
  width: 150px;
  height: 150px;
  bottom: 1vh;
  left: 1vh;
  border-radius: 3px;
  z-index: 100;
}
</style>
