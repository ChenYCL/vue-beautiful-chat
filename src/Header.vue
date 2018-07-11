<template>
  <div class="sc-header" :style="style">
    <img class="sc-header--img" v-if="imageUrl" :src="imageUrl" alt="" />
    <div class="sc-header--team-name"> 
      {{teamName}}
      <span v-if="isTyping" class="typing"> sta scrivendo <span>.</span><span>.</span><span>.</span></span> 
    </div>
    <div class="sc-header--close-button" @click="onClose">
      <img src="./assets/close-icon.png" alt="" />
    </div>
  </div>
</template>
<script>
export default {
  props: {
    imageUrl: {
      type: String,
    },
    teamName: {
      type: String
    },
    onClose: {
      type: Function,
      required: true
    },
    mainColor: {
      type: String,
    },
    isTyping: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    style () {
      return 'background-color: ' + this.mainColor;
    }
  }
}
</script>
<style scoped>
.sc-header {
  min-height: 75px;
  border-top-left-radius: 9px;
  border-top-right-radius: 9px;
  color: white;
  padding: 10px;
  box-shadow: 0 1px 4px rgba(0,0,0,.2);
  position: relative;
  box-sizing: border-box;
  display: flex;
}

.sc-header--img {
  border-radius: 50%;
  align-self: center;
  padding: 10px;
  max-width: 100%;
  max-height: 100%;
}

.sc-header--team-name {
  align-self: center;
  padding: 10px;
  flex: 1;
  user-select: none;
  cursor: pointer;
  border-radius: 5px;
}

.sc-header--close-button {
  width: 40px;
  align-self: center;
  height: 40px;
  margin-right: 10px;
  box-sizing: border-box;
  cursor: pointer;
  border-radius: 5px;
}

.sc-header--close-button img {
  width: 100%;
  height: 100%;
  padding: 13px;
  box-sizing: border-box;
}

@media (max-width: 450px) {
  .sc-header {
    border-radius: 0px;
  }
}

@keyframes blink {
    0% {
      opacity: .2;
    }
    20% {
      opacity: 1;
    }
    100% {
      opacity: .2;
    }
}

.typing span {
    animation-name: blink;
    animation-duration: 1.4s;
    animation-iteration-count: infinite;
    animation-fill-mode: both;
}

.typing span:nth-child(2) {
    animation-delay: .2s;
}

.typing span:nth-child(3) {
    animation-delay: .4s;
}

</style>
