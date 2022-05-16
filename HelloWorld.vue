<template>
  <div class="container">
    <v-btn class="primary" @click="onButtonClick">
      Button
    </v-btn>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',

  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    onButtonClick () {
      this.$router.replace('/card')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.primary {
    background-color: #1867c0 !important;
    border-color: #1867c0 !important;
}
</style>
