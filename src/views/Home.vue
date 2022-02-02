<template>
<div class="h__100">
    <Login v-show="!setlogin_userFromStore"/>
  <home-graph v-show="setlogin_userFromStore" class="fadeIn__base"></home-graph>
</div>
</template>

<script>
import Login from '../views/Login.vue'
import homeGraph from '../components/home/homeGraph.vue'
import store from '../store'
export default {
    name: 'Home',
    components: {
      Login,
      homeGraph
    },
    store,
  async fetch() {
      await this.$store.dispatch('costs/choiceCosts')
      console.log('到達してるよ')
  },
  computed:{
    setlogin_userFromStore() {
      return this.$store.getters['users/setLogin_user']
    },
   },
  }

</script>
<style scoped>
@import '../scss/animation.scss';
@import '../scss/space.scss';
.h__100 {
  height: 100%;
}
.chart{
  max-width: 700px;
}

</style>


