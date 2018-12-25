<template>
  <div class='sc-message' >
    <!--<div class='sc-message&#45;&#45;file-icon'>-->
      <!--<a :href="data.file.url || '#'" target='_blank'>-->
        <!--<img src="./assets/file.svg" alt='generic file icon' height="60" />-->
        <img :src="base64" alt='generic file icon' height="100%" width="100%"/>
      <!--</a>-->
    <!--</div>-->
    <!--<div class='sc-message&#45;&#45;file-name' :style="messageColors">-->
      <!--<a :href="data.file.url ? data.file.url : '#'" target='_blank'>{{data.file.name || ''}}</a>-->
    <!--</div>-->
    <!--<div class="sc-message&#45;&#45;file-text" :style="messageColors">{{data.text}}<p v-if="data.meta" class='sc-message&#45;&#45;meta' :style="messageColors">{{data.meta}}</p></div>-->
  </div>
</template>

<script>
export default {
  data(){
    return {
      base64:''
    }
  },
  props: {
    data: {
      type: Object,
      required: true
    },
    messageColors: {
      type: Object,
      required: true
    }
  },
  created(){
    let that =this;
    let reader = new FileReader();
    reader.readAsDataURL(this.data.file);
    reader.onloadend = function() {
      that.base64 = reader.result; // base64
      // console.log(that.base64)
    };

  }
}
</script>

<style scoped>
.sc-message--file {
  border-radius: 6px;
  font-weight: 300;
  font-size: 14px;
  line-height: 1.4;
  /* white-space: pre-wrap; */
  -webkit-font-smoothing: subpixel-antialiased
}

.sc-message--content.sent .sc-message--file {
  word-wrap: break-word;
}

.sc-message--file-icon {
  text-align: center;
  margin-left: auto;
  margin-right: auto;
  margin-top: 15px;
  margin-bottom: 0px;
}

.sc-message--file-icon:hover {
  opacity: 0.7;
}

.sc-message--file-text {
  padding: 17px 20px;
  border-radius: 6px;
  font-weight: 300;
  font-size: 14px;
  line-height: 1.4;
  white-space: pre-wrap;
  -webkit-font-smoothing: subpixel-antialiased
}

.sc-message--file-name {
  color: white;
  padding-left: 15px;
  padding-right: 15px;
  padding-top: 0;
  font-size: x-small;
  text-align: center;
}

.sc-message--file-name a {
  text-decoration: none;
  color: #ece7e7;
}

.sc-message--file-name a:hover {
  color: white;
}

.sc-message--content.sent .sc-message--file-text {
  color: white;
  background-color: #4e8cff;
  word-wrap: break-word;
}

.sc-message--content.received .sc-message--file {
  color: #263238;
  background-color: #f4f7f9;
  margin-right: 40px;
}

.sc-message--content.received .sc-message--file-name {
  color: #000;
}

.sc-message--content.received .sc-message--file a {
  color: rgba(43, 40, 40, 0.7);
}

.sc-message--content.received .sc-message--file a:hover {
  color: #0c0c0c;
}
</style>
