<template>
  <div class="sc-message--text">
  <p>
  	<p v-if="data.sender" class="sc-message--sender"> {{data.sender}}</p>{{data.text}}
  </p>
  <p v-if="data.meta" class='sc-message--meta'>{{data.meta}}</p>
  <p class='sc-message--time' v-if="data.time"> {{data.time}}</p></div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>



</style>
